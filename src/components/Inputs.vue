<template>
  <div>
    <div class='title'>Inputs</div>
    <div class='input-border' v-for='input in inputs'>
      <div class='col full'>
        <input type='text' class='link' placeholder="Enter link to image here" v-model='input.link' autocomplete="off" autocorrect="off" autocapitalize="off" spellcheck="false" @change='input.updateBinding()'>
        <div class='label'>{{input.name}}</div>
      </div>
      <div v-if='input.error'>
        Error!
      </div>
    </div>
    <div v-if='canAddMore'><a href="#" @click.prevent='addInput()'>Add image</a></div>
  </div>
</template>

<script>
export default {
  name: 'Inputs',
  props: ['vm'],
  computed: {
    canAddMore() {
      return this.inputs.length < 1;
    }
  },
  data() {
    var vm = this.vm;
    return {
      inputs: vm.getInputs(),
      addInput: vm.addInput
    };
  },
  methods: {
    onSubmit() {
      
    }
  }
}
</script>

<style lang="stylus">
@import "./shared.styl";

.input-border {
  margin-top: 10px;
  padding-top: 10px;

  .label {
    font-size: small;
    color: ternary-text;
  }

  input[type='text'].link {
    margin-left: 0;
    &:focus {
      outline: none;
      border: 0px transparent;
    }
    &::placeholder {
      color: ternary-text;
    }
  }
}
</style>
