<template>
      <div class="inputBlock">

      <input type="text"
             v-model="input.value"
             v-bind:placeholder="input.placeholder"
             v-bind:class="input.class"
             v-on:keyup="validateValue"
      />
      <div class="inputBlock-error">
        {{ input.errorMsg }}
      </div>
      <div class="inputBlock-content">
        {{ input.value }}
      </div>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    </div>



</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'



export default {
    name: 'InputBlock',
    data() {
        return {
            'input': {
                'value': '',
                'class': '',
                'placeholder': 'Entre un texte',
                'errorMsg' : ''
            }
        }
    },
    methods: {
        validateValue() {
            this.input.errorMsg += (this.input.value.length > 3) ?
                '' : ' - trop court '
            this.input.errorMsg += (this.input.value.match(/[a-z]+/)) ?
                '' : ' - manque une minuscule '
            this.input.errorMsg += (this.input.value.match(/[A-Z]+/)) ?
                '' : ' - manque une majuscule '
            this.input.errorMsg += (this.input.value.match(/[\d]+/)) ?
                '' : ' - Il faut au moins 1 chiffre '
        }
    }
}

</script>
<style>
    .inputBlock input {
        padding: 6px 10px;
    }
    .inputBlock-content {
        padding-top: 10px;
    }
    .input-error {
        outline-color: indianred;
        color: indianred;
    }
</style>
