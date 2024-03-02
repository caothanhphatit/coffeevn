<template>
    <v-card>
      <v-container fluid>
        <v-row>
          <v-col v-for="card in cards" :key="card.title" :cols="card.flex">
            <v-card>
              <a @click.prevent="navigateToTab(card.tabIndex)" class="link-no-style">
                <v-img
                  :src="card.src"
                  class="align-end"
                  gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                  height="400px"
                  cover
                >
                <v-card-title class="text-white" v-text="card.title" style="font-size: 40px; font-style:italic"></v-card-title>
                </v-img>
              </a>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
  </template>
  
  <script>
  export default {
    data: () => ({
      cards: [
        {
          title: 'Nơi thiết kế phin coffee theo phong cách của bạn',
          src: 'https://www.alliancecoffee.net/wp-content/uploads/2021/04/phin-guide-1024x536.jpg',
          flex: 12,
          link: 'https://example.com/card1',
          tabIndex: 1 // index of the tab to navigate to
        },
        {
          title: 'Tận hưởng các hương vị đặc biệt của cà phê Việt',
          src: 'https://cdn.tgdd.vn/Files/2021/12/02/1401913/trung-nguyen-co-nhung-loai-ca-phe-hoa-tan-nao-loai-nao-ngon-nhat-202112021358385906.jpg',
          flex: 6,
          link: 'https://example.com/card1',
          tabIndex: 2 // index of the tab to navigate to
        },  
        {
          title: 'Truy cập các kênh mua hàng của chúng tôi để được nhận ngay ưu đãi ...',
          src: 'https://cafefcdn.com/thumb_w/640/203337114487263232/2023/1/26/photo1674695780244-16746957803322024846374.png',
          flex: 6,
          link: 'https://example.com/card1',
          tabIndex: 2 // index of the tab to navigate to
        },
      ],
    }),
    methods: {
      navigateToTab(tabIndex) {
        this.$emit('navigateToTab', tabIndex);
      }
    }
  }
  </script>
  
  <style scoped>
  .link-no-style {
    text-decoration: none; /* Remove default underline */
    outline: none; /* Remove default outline */
  }
  </style>
  