<template>
  <v-card>
    <v-toolbar color="#abb0fc" style="height:65px;">
      <v-text-field
        class="mx-4"
        flat
        hide-details
        label="Search..."
        prepend-inner-icon="mdi-magnify"
        solo-inverted
      ></v-text-field>
    </v-toolbar>
    <v-carousel>
      <v-carousel-item
        v-for="(item, i) in items"
        :key="i"
        :src="item.src"
        reverse-transition="fade-transition"
        transition="fade-transition"
      ></v-carousel-item>
    </v-carousel>
  </v-card>
</template>

<script>
// import Logo from '~/components/Logo.vue'
// import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  data() {
    return {
      tabs: null,
      items: [
        {
          src:
            'https://64.media.tumblr.com/8afc260a67675b4ec6c3e0328e13cec3/tumblr_phwpnhdwEl1tt6f8lo1_1280.jpg',
        },
        {
          src:
            'https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/549e9b77-4c90-4c7f-8d0e-772a4ba70576/d3fqoiw-33a74a57-ef9b-4eea-ba95-4a95227bd10a.jpg/v1/fill/w_1192,h_671,q_70,strp/club_of_aircraft_modeling_by_arsenixc_d3fqoiw-pre.jpg?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOiIsImlzcyI6InVybjphcHA6Iiwib2JqIjpbW3siaGVpZ2h0IjoiPD03ODgiLCJwYXRoIjoiXC9mXC81NDllOWI3Ny00YzkwLTRjN2YtOGQwZS03NzJhNGJhNzA1NzZcL2QzZnFvaXctMzNhNzRhNTctZWY5Yi00ZWVhLWJhOTUtNGE5NTIyN2JkMTBhLmpwZyIsIndpZHRoIjoiPD0xNDAwIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmltYWdlLm9wZXJhdGlvbnMiXX0.F_B-MCA-P2eE93EDpLD_J8RhxcbQlCNYlnfW9da1UNA',
        },
        {
          src:
            'https://pbs.twimg.com/media/ELS1UAkUUAIoKQ2?format=jpg&name=large',
        },
        {
          src:
            'https://pbs.twimg.com/media/ELS1UAmUcAIECI6?format=jpg&name=large',
        },
      ],
    }
  },
}

// export default {
//   components: {
//     Logo,
//     VuetifyLogo,
//   },
// }
</script>
