<template>
  <cookie-control-functional
    v-slot="{ isReady, show, modal, cookies }"
    locale="en"
    :reloadDelay="600"
    :override-optional-cookies="cookiesOverride.optional"
    :override-necessary-cookies="cookiesOverride.necessary"
    :overrid-expiration-date="cookiesOverride.expirationDate"
  >
    <transition>
      <div v-if="isReady && show" class="cookie-control__container">
        <div class="cookie-control__wrapper">
          <cookie-control-header :bar-description="cookiesOverride.barDescription" />
          <cookie-control-accordeon :cookies="cookies" :expand="modal" />
          <cookie-control-footer :cookies="cookies" :modal="modal" />
        </div>
      </div>
    </transition>
  </cookie-control-functional>
</template>
<script>
import CookieControlAccordeon from './cookieControlAccordeon'
import CookieControlHeader from './cookieControlHeader'
import CookieControlFooter from './cookieControlFooter'

export default {
  name: 'CookieControl',
  components: {
    CookieControlAccordeon,
    CookieControlHeader,
    CookieControlFooter,
  },
  data() {
    return {
      cookiesOverride: {
        // This overrides the data from the config
        // It can come from anywhere eg. async data / CMS
        // It is important to keep the shape of the optional and neccesary object as following
        optional: [
          {
            name: 'Optionele Cookies',
            description:
              '<div class="article"><p class="">Deze cookies worden geïmplementeerd om ons in staat te stellen het gedrag van bezoekers te analyseren, zodat wij hen in de toekomst beter van dienst kunnen zijn. Alle gegevens die worden verzameld, worden anoniem opgeslagen en kunnen niet worden herleid tot de bezoeker.</p></div>',
            cookies: ['_ga_GTM-K9WL7T7', '_ga', '_gid'],
            // Function to call when script accepted
            // Must be a Sting
            accepted:
              "window.dataLayer = window.dataLayer || []; function gtag(){dataLayer.push(arguments);} gtag('js', new Date()); gtag('config', 'GTM-K9WL7T7');",
            declined: "window['ga-disable-GTM-K9WL7T7'] = true;",
            // Script to load when accepted
            src: 'https://www.googletagmanager.com/gtag/js?id=GTM-K9WL7T7',
            async: true,
          },
        ],
        necessary: [
          {
            name: 'Noodzakelijke Cookies',
            description:
              '<p>Deze cookies zijn nodig voor de functionaliteit van de website en kunnen daarom niet worden uitgezet. Bijvoorbeeld de taalvoorkeur van de gebruiker in een meertalige omgeving. Indien u ook deze cookies wenst te blokkeren, dient u de acceptatie van cookies uit te schakelen in uw browserinstellingen. Let op: hierdoor kan deze website ongevoelig worden of kunnen bepaalde functies ontoegankelijk worden. Functionele cookies slaan nooit zoveel persoonlijke informatie op dat u als gebruiker geïdentificeerd kunt worden; alle informatie is anoniem.</>',
            cookies: ['cookie_control_enabled_cookies', 'cookie_control_consent'],
          },
        ],
        barDescription:
          '<p>Deze website maakt gebruik van cookies. Sommige van deze cookies zijn functioneel en kunnen niet worden geweigerd. Andere cookies dienen om het gebruik van deze website te analyseren, om uw klantervaring te optimaliseren en/of om u gepersonaliseerde informatie te verstrekken. Verder implementeren wij ook cookies voor de integratie van sociale media, video of van derden. Kies een van de onderstaande opties om het gebruik te verfijnen of om alle cookies te accepteren.</>',
        expirationDate: 3,
      },
    }
  },
}
</script>
<style lang="scss">
.cookie-control {
  position: relative;
  color: white;

  &::after {
    content: '';
    position: fixed;
    width: 100vw;
    height: 100vh;
    top: 0;
    left: 0;
    z-index: 999;
    background-color: rgba(black, 0.5);
    pointer-events: none;
    opacity: 0;
    transition: all 400ms cubic-bezier(0.36, 1, 0.22, 1);
  }

  &.modal-open::after {
    opacity: 1;
  }

  &__container {
    display: flex;
    justify-content: center;

    position: fixed;
    z-index: 1000;
    bottom: 1rem;
    left: 0;

    padding: 0 1rem;
    width: 100%;
    max-height: 75vh;
    margin-bottom: env(safe-area-inset-bottom, 0);

    pointer-events: none;
    overflow: hidden;
    transform: translate3d(0, 0, 0);

    transition: all 800ms cubic-bezier(0.22, 1, 0.36, 1);

    &.v-enter,
    &.v-leave-to {
      transform: translate3d(0, 150%, 0);
      transition: all 800ms cubic-bezier(0.22, 1, 0.36, 1);
    }

    &.v-leave-to,
    &.v-enter {
      transform: translate3d(0, 150%, 0);
      transition: all 800ms cubic-bezier(0.22, 1, 0.36, 1);
    }

    &.v-leave {
      transform: translate3d(0, 0, 0);
      transition: all 800ms cubic-bezier(0.22, 1, 0.36, 1);
    }
  }

  &__wrapper {
    width: 100%;
    pointer-events: none;

    display: flex;
    flex-direction: column;
    justify-content: flex-end;
  }
}
</style>
