<template>
    <div>
        <v-container>
            <v-row>
                <v-col>
                    <v-btn
                        variant="elevated"
                        @click="storeClickTime" 
                    >
                        Store click time
                    </v-btn>
                    <ul>
                        <li v-for="(time, index) in clickTimes" :key="index">{{ time }}</li>
                    </ul>
                </v-col>
            </v-row>
            <v-row>
                <v-col>
                  <v-form @submit.prevent="submitForm">
                    <input v-model="name" type="text" placeholder="Your name" />
                    <input v-model="email" type="email" placeholder="Your email" />
                    <v-btn
                        type="submit"
                        variant="elevated"
                    >
                        Send
                    </v-btn>                    
                    <p>{{ errorMessage }}</p>
                </v-form>
              </v-col>
            </v-row>
            <v-row>
                <v-col>
                  <v-btn
                        variant="elevated"
                        @click="chengeHandler" 
                    >
                        Change click handler
                    </v-btn>
                    <v-btn
                        variant="elevated"
                        @click="handlerClick" 
                    >
                        Check handler by {{ methodName }}
                    </v-btn>                                      
              </v-col>
            </v-row>
        </v-container>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        clickTimes: [],
        name: '',
        email: '',
        errorMessage: '',
        useMothod1: true,
        methodName: 'Method 1',
      };
    },
    methods: {
      storeClickTime() {
        const currentTime = new Date();
        this.clickTimes.push(currentTime);
      },
      submitForm() {
        if (this.name && this.email.includes('@') && this.email.includes('.')) {
          alert(`Name: ${this.name}, Email: ${this.email}`);
          this.errorMessage = '';
        } else {
          this.errorMessage = 'Enter correct name and email';
        }
      },
      chengeHandler() {
        this.useMothod1 = !this.useMothod1;  
        this.methodName = this.useMothod1 ? 'Method 1' : 'Method 2';
      },
      handlerClick() {
        if (this.useMothod1) {
          alert("Uses method 1");
        } else {
          alert("Uses method 2");
        }
      },

    }
  };
  </script>