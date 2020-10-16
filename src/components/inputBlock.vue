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
    </div>
</template>
<script>
    export default {
        name: 'InputBlock',
        data() {
            return {
                'input': {
                    'value': '',
                    'class': '',
                    'placeholder': 'Valeur',
                    'errorMsg' : ''
                }
            }
        },
        methods: {
            validateValue() {
               this.input.errorMsg += (this.input.value.length > 3) ?
                    '' : 'trop court'
                this.input.errorMsg += (this.input.value.match(/[a-z]+/)) ?
                    '' : 'manque une minuscule'
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