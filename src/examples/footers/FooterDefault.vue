<script setup>
import logoDark from "@/assets/img/logo-ct-dark.png";
defineProps({
  brand: {
    type: Object,
    name: String,
    logo: String,
    route: "",
    default: () => ({
      name: "AntiochDAO",
      logo: logoDark,
      route: "/"
    })
  },
  socials: {
    type: Array,
    icon: String,
    link: String,
    default: () => [
      {
        icon: '<i class="fab fa-twitter text-lg opacity-8"></i>',
        link: "https://twitter.com/AntiochDAO"
      },
      {
        icon: '<i class="fab fa-github text-lg opacity-8"></i>',
        link: "https://github.com/AntiochDAO"
      },
      // {
      //   icon: '<i class="fab fa-youtube text-lg opacity-8"></i>',
      //   link: "https://www.youtube.com/channel/UCVyTG4sCw-rOvB9oHkzZD1w"
      // }
    ]
  },
  menus: {
    type: Array,
    name: String,
    items: {
      type: Array,
      name: String,
      href: String
    },
    default: () => [
      {
        name: "about us",
        items: [
          {
            name: "Ken Hodler",
            href: "https://twitter.com/bgok"
          },
        ]
      },
      {
        name: "resources",
        items: [
          {
            name: "Scaling Ethereum Hackathon 2023",
            href: "https://ethglobal.com/events/scaling2023"
          },
          { name: "Filecoin Virtual Machine", href: "https://fvm.filecoin.io/" },
          {
            name: "OpenZeppelin Governor",
            href: "https://docs.openzeppelin.com/contracts/4.x/api/governance"
          },
          {
            name: "TableLand",
            href: "https://tableland.xyz/"
          }
        ]
      },
      {
        name: "",
        items: []
      },
      {
        name: "help & support",
        items: [
          {
            name: "report an issue",
            href: "https://github.com/AntiochDAO/AntiochDAO/issues/new/choose"
          },
          {
            name: "contact us",
            href: "sendto:info@antiochdao.com"
          },
        ]
      },
    ]
  }
});
</script>
<template>
  <footer class="footer pt-5 mt-5">
    <div class="container">
      <div class="row">
        <div class="col-md-3 mb-4 ms-auto">
          <div>
            <a :href="brand.route">
              <img :src="brand.logo" class="mb-3 footer-logo" alt="main_logo" />
            </a>
            <h6 class="font-weight-bolder mb-4">{{ brand.name }}</h6>
          </div>
          <div>
            <ul class="d-flex flex-row ms-n3 nav">
              <li
                class="nav-item"
                v-for="{ icon, link } of socials"
                :key="link"
              >
                <a
                  class="nav-link pe-1"
                  :href="link"
                  target="_blank"
                  v-html="icon"
                >
                </a>
              </li>
            </ul>
          </div>
        </div>
        <div
          class="col-md-2 col-sm-6 col-6 mb-4"
          v-for="{ name, items } of menus"
          :key="name"
        >
          <h6 class="text-sm">{{ name }}</h6>
          <ul class="flex-column ms-n3 nav">
            <li class="nav-item" v-for="item of items" :key="item.name">
              <a class="nav-link" :href="item.href" target="_blank">
                {{ item.name }}
              </a>
            </li>
          </ul>
        </div>

        <div class="col-12">
          <div class="text-center">
            <p class="text-dark my-4 text-sm font-weight-normal">
              All rights reserved. Copyright ©
              {{ new Date().getFullYear() }}
              AntiochDAO by
              <a href="https://twitter.com/bgok" target="_blank"
                >Ken Hodler</a
              >.
            </p>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>
