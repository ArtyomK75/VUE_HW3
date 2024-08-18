<template>
  <div>
    <v-container>
      <v-row>
        <v-row>
          <v-col v-for="(item, index) in items" :key="index" :style="getRandomStyle()">
            {{ item }}
          </v-col>
        </v-row>
      </v-row>
      <v-row>
        <div :style="boxStyle" class="box"></div>
        <v-btn
          variant="elevated"
          @click="animateBox" 
        >
          Change style
        </v-btn>                                      
      </v-row>
      <v-row>
        <v-btn
          variant="elevated"
          @click="changeTheme" 
        >
          Change theme
        </v-btn>                                      
      </v-row>
   </v-container>
  </div>
</template>
  
<script>
  export default {
    props: ['theme'],
    data() {
      return {
        items: ['Item 1', 'Item 2', 'Item 3', 'Item 4', 'Item 5', 'Item 6', 'Item 7', 'Item 8', 'Item 9'],
        boxStyle: {
          width: '100px',
          height: '100px',
          backgroundColor: 'red',
          transition: 'all 0.5s ease'
        },
        lockalTheme: '',
      }
    },
    methods: {
      getRandomStyle() {
        const randomColor = `#${Math.floor(Math.random() * 16777215).toString(16)}`;
        const randomFontSize = `${Math.floor(Math.random() * 20) + 14}px`;
        return {
          backgroundColor: randomColor,
          fontSize: randomFontSize
        };
      },
      animateBox() {
        this.boxStyle = {
          width: `${Math.floor(Math.random() * 200) + 50}px`,
          height: `${Math.floor(Math.random() * 200) + 50}px`,
          backgroundColor: `#${Math.floor(Math.random() * 16777215).toString(16)}`,
          transition: 'all 0.5s ease'
        };
      },
      changeTheme() {
        this.$emit('theme-chenged', this.theme === 'light' ? 'dark' : 'light');        
      },
    }
  };
</script>

