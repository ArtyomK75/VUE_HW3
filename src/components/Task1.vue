<template>
    <div>
        <h2>Change boolean value</h2>
        <v-container>
            <v-row>
                <v-col>
                    <v-btn
                        variant="text"
                        @click="boolValue = !boolValue" 
                    >
                        Change boolean value
                    </v-btn>
                    <h3>{{ messageBollVal +  boolValue}}</h3>
                </v-col>
            </v-row>
            <v-row>
                <label>
                    <input type="checkbox" v-model="isDisabled" />
                        Blocked input
                </label>
                <label>                
                    <input type="checkbox" v-model="isReadOnly" />
                        Make inpun "Read only"
                </label>

                <input 
                    type="text" 
                    :disabled="isDisabled" 
                    :readonly="isReadOnly"
                    placeholder="Input text"/>
                </input>
            </v-row>
        </v-container>
    </div>
</template>

<script>
    export default {
        name: 'Task1',
        data () {
            return {
                boolValue: false,
                messageBollVal: "boolean value is ",
                isDisabled: false,
                isReadOnly: false,
            }
        },
        methods: {
        }
    };
</script>


