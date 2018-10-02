<template>
  <section>
    <header class="elevation-2">
      <img src="~/static/images/icons/icon.png" alt="" class="icon">
      <div id="title">
        <img src="~/static/images/title.svg" alt="YOKO KARASAKI"/>
      </div>
      <nav>
        <ul>
          <li class="github">
            <a href="https://github.com/KarageAgeta" target="_blank" rel="noopener">
              <img src="~/static/images/icons/ic_github_outline.svg" alt="GitHub"/>
            </a>
          </li>
          <li class="blog">
            <a href="http://karage-ageta.hatenablog.com/" target="_blank" rel="noopener">
              <img src="~/static/images/icons/ic_pencil_outline.svg" alt="Blog"/>
            </a>
          </li>
          <li class="twitter">
            <a href="https://twitter.com/KarageAgeta" target="_blank" rel="noopener">
              <img src="~/static/images/icons/ic_twitter_outline.svg" alt="Twitter"/>
            </a>
          </li>
        </ul>
      </nav>
    </header>
    <main>
      <nuxt/>
    </main>
    <footer>
    </footer>
  </section>
</template>

<style lang="scss">
  html {
    font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    font-size: 16px;
    color: $primary-text-color;
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
    padding-bottom: $spacing-small;
    background: $light-background;
    background: linear-gradient(315deg, rgba(7, 33, 42, 0.9) 0%, rgba(14, 70, 90, 0.9) 100%);
    width: 100%;
    position: relative;
    top: 0;
    text-align: center;

    a {
      color: $light-background;
      font-weight: bold;
    }

    nav {
      margin-top: $spacing-x-small;

      ul {
        margin: unset;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-areas: "github blog twitter";

        li {
          display: inline;

          &.github {
            grid-area: github;
          }

          &.blog {
            grid-area: blog;
          }

          &.twitter {
            grid-area: twitter;
          }

          img {
            width: 4vw;
            min-width: 32px;
            max-width: 40px;
          }
        }
      }

      @media (min-width: 768px) {
        ul {
          grid-template-columns: 2fr 1fr 1fr 1fr 2fr;
          grid-template-areas: ". github blog twitter .";
        }
      }
    }

    .icon {
      width: 32vw;
      min-width: 120px;
      max-width: 200px;
      border-radius: 50%;
      border: solid 8px $light-background;
      margin-top: $spacing-small;
    }

    #title {
      color: $light-background;
      font-size: 48px;
      margin-top: $spacing-x-small;

      img {
        width: 48vw;
        min-width: 320px;
        max-width: 480px;
      }
    }
  }
</style>
