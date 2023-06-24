<script lang="ts">
  import { setupConfig } from "@ionic/core";

  class PageOne extends HTMLElement {
    connectedCallback() {
      this.innerHTML = `
    <ion-header>
      <ion-toolbar>
        <ion-title>Page One</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      This is the content for page 1.
      <ion-router-link href="/page-two">
        <ion-button>Go to Page 2</ion-button>
      </ion-router-link>
    </ion-content>`;
    }
  }

  class PageTwo extends HTMLElement {
    connectedCallback() {
      this.innerHTML = `
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button default-href="/"></ion-back-button>
        </ion-buttons>
        <ion-title>Page Two</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      This is the content for page 2.
    </ion-content>`;
    }
  }

  customElements.define("page-one", PageOne);
  customElements.define("page-two", PageTwo);

  setupConfig({
    mode: "ios",
  });
</script>

<ion-app>
  <ion-router>
    <ion-route url="/" component="page-one" />
    <ion-route url="/page-two" component="page-two" />
  </ion-router>

  <ion-router-outlet />
</ion-app>
