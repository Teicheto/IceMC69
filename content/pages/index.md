---
type: PageLayout
title: Начало
colors: colors-a
backgroundImage:
  type: BackgroundImage
  url: /images/bg1.jpg
  backgroundSize: cover
  backgroundPosition: center
  backgroundRepeat: no-repeat
  opacity: 75
sections:
  - elementId: ''
    colors: colors-f
    backgroundSize: full
    title: >-
      Здравей и добре дошъл в едно уникално майнкрафт сървърче а именно ->> IceMC
    subtitle: >-
      <div>
        <p>IP: <strong id="ip-address">play.icemc.online</strong> <button class="btn" onclick="copyIP('play.icemc.online')">Копирай IP</button></p>
        <p>Port: <strong id="port-address">25565</strong> <button class="btn" onclick="copyPort()">Копирай Порт</button></p>
        <p>Активни играчи: <span id="players-online">Зареждане...</span></p>
      </div>
    styles:
      self:
        height: auto
        width: wide
        margin:
          - mt-0
          - mb-0
          - ml-0
          - mr-0
        padding:
          - pt-36
          - pb-48
          - pl-4
          - pr-4
        flexDirection: row-reverse
        textAlign: left
    type: HeroSection
    actions: []
  - colors: colors-f
    type: FeaturedProjectsSection
    elementId: ''
    actions:
      - type: Link
        label: See all projects
        url: /projects
    showDate: false
    showDescription: true
    showFeaturedImage: true
    showReadMoreLink: true
    variant: variant-b
    projects:
      - content/pages/projects/project-two.md
      - content/pages/projects/project-three.md
      - content/pages/projects/project-one.md
    styles:
      self:
        height: auto
        width: wide
        padding:
          - pt-24
          - pb-24
          - pl-4
          - pr-4
        textAlign: left
    subtitle: Projects
  - type: FeaturedPostsSection
    elementId: ''
    colors: colors-f
    variant: variant-d
    subtitle: Featured Posts
    showFeaturedImage: false
    actions:
      - type: Link
        label: See all posts
        url: /blog
    posts:
      - content/pages/blog/post-six.md
      - content/pages/blog/post-four.md
      - content/pages/blog/post-three.md
    showDate: true
    showExcerpt: true
    showReadMoreLink: true
    styles:
      self:
        height: auto
        width: narrow
        padding:
          - pt-28
          - pb-48
          - pl-4
          - pr-4
        textAlign: left
  - type: ContactSection
    colors: colors-f
    backgroundSize: full
    title: "Got an interesting project? Tell me more...\U0001F4AC"
    form:
      type: FormBlock
      elementId: sign-up-form
      fields:
        - name: firstName
          label: First Name
          hideLabel: true
          placeholder: First Name
          isRequired: true
          width: 1/2
          type: TextFormControl
        - name: lastName
          label: Last Name
          hideLabel: true
          placeholder: Last Name
          isRequired: false
          width: 1/2
          type: TextFormControl
        - name: email
          label: Email
          hideLabel: true
          placeholder: Email
          isRequired: true
          width: 1/2
          type: EmailFormControl
        - name: address
          label: Address
          hideLabel: true
          placeholder: Address
          isRequired: true
          width: 1/2
          type: TextFormControl
        - name: updatesConsent
          label: Sign me up to recieve updates
          isRequired: false
          width: full
          type: CheckboxFormControl
      submitLabel: "Submit \U0001F680"
      styles:
        self:
          textAlign: center
    styles:
      self:
        height: auto
        width: narrow
        margin:
          - mt-0
          - mb-0
          - ml-0
          - mr-0
        padding:
          - pt-24
          - pb-24
          - pr-4
          - pl-4
        flexDirection: row
        textAlign: left
  - type: CustomHTMLSection
    title: Активни играчи и IP
    subtitle: >-
      <p>IP: <strong id="ip-address">play.icemc.online</strong> <button class="btn" onclick="copyIP('play.icemc.online')">Копирай IP</button></p>
      <p>Port: <strong id="port-address">25565</strong> <button class="btn" onclick="copyPort()">Копирай Порт</button></p>
      <p>Активни играчи: <span id="players-online">Зареждане...</span></p>
    styles:
      self:
        padding:
          - pt-24
          - pb-24
          - pl-4
          - pr-4
    html:
      content: |
        <script>
            // Функция за зареждане на активни играчи
            async function fetchPlayers() {
                try {
                    let response = await fetch(`https://mcapi.us/server/status?ip=play.icemc.online`);
                    let data = await response.json();
                    if (data.online) {
                        document.getElementById("players-online").innerText = data.players.now;
                    } else {
                        document.getElementById("players-online").innerText = "Сървърът е офлайн";
                    }
                } catch (error) {
                    document.getElementById("players-online").innerText = "Грешка при зареждане";
                }
            }
            fetchPlayers();

            // Функция за копиране на IP адрес
            function copyIP(ip) {
                navigator.clipboard.writeText(ip).then(() => {
                    alert("IP адресът е копиран: " + ip);
                }).catch(err => {
                    console.error("Грешка при копиране: ", err);
                });
            }

            // Функция за копиране на Порт
            function copyPort() {
                const port = "25565"; // Порт
                navigator.clipboard.writeText(port).then(() => {
                    alert("Портът е копиран: " + port);
                }).catch(err => {
                    console.error("Грешка при копиране на порт: ", err);
                });
            }
        </script>
    actions: []
---
