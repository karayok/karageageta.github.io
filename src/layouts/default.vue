<template>
  <div>
    <div class="main">
      <header>
        <vs-row vs-align="center" vs-type="flex" vs-justify="space-around" vs-w="12">
          <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="2">
            <img src="~/static/images/icons/icon.png" alt="" class="icon">
          </vs-col>
        </vs-row>
        <vs-row id="title" vs-align="center" vs-type="flex" vs-justify="space-around" vs-w="12">
          <img src="~/static/images/title.svg" alt="YOKO KARASAKI"/>
        </vs-row>
        <nav>
          <vs-row vs-align="center" vs-type="flex" vs-justify="space-around" vs-w="12">
            <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-lg="3" vs-sm="4" vs-xs="5">
              <vs-row vs-align="center" vs-type="flex" vs-justify="space-around" vs-w="12">
                <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="1">
                  <a href="https://github.com/KarageAgeta" target="_blank" rel="noopener">
                    <img src="~/static/images/icons/ic_github_outline.svg" alt="GitHub"/>
                  </a>
                </vs-col>
                <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="1">
                  <a href="http://karage-ageta.hatenablog.com/" target="_blank" rel="noopener">
                    <img src="~/static/images/icons/ic_pencil_outline.svg" alt="Blog"/>
                  </a>
                </vs-col>
                <vs-col vs-type="flex" vs-justify="center" vs-align="center" vs-w="1">
                  <a href="https://twitter.com/KarageAgeta" target="_blank" rel="noopener">
                    <img src="~/static/images/icons/ic_twitter_outline.svg" alt="Twitter"/>
                  </a>
                </vs-col>
              </vs-row>
            </vs-col>
          </vs-row>
        </nav>
      </header>
      <section>
        <nuxt/>
      </section>
    </div>
    <footer>
    </footer>
  </div>
</template>

<style lang="scss">
  html {
    font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    font-size: 16px;
    color: rgb(38, 50, 56);
    word-spacing: 1px;
    -ms-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    box-sizing: border-box;
  }

  *, *:before, *:after {
    box-sizing: border-box;
    margin: 0;
  }

  header {
    background: rgb(7, 33, 42);
    background: linear-gradient(315deg, rgba(7, 33, 42, 0.9) 0%, rgba(14, 70, 90, 0.9) 100%);
    width: 100%;
    height: 40vw;
    min-height: 288px;
    max-height: 344px;
    position: relative;

    nav {
      margin-top: 24px;

      img {
        width: 4vw;
        min-width: 32px;
        max-width: 40px;
      }
    }

    a {
      color: #fff;
      font-weight: bold;
    }

    .icon {
      width: 32vw;
      min-width: 120px;
      max-width: 152px;
      border-radius: 50%;
      border: solid 8px #fff;
      margin-top: 32px;
    }

    #title {
      color: #fff;
      font-size: 48px;
      margin-top: 24px;

      img {
        width: 48vw;
        min-width: 320px;
        max-width: 480px;
      }
    }
  }

  .main {
    width: 100%;
    min-height: calc(100vh - 60px);
  }

  section {
    margin: 24px auto;
  }
</style>
