<template>
  <li>
    <span>{{ todo.text }}</span>
    <span class="icon" @click.prevent="$emit('remove', todo)"><img src="https://img.icons8.com/metro/15/000000/cancel.png"/></span>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      required: true,
      type: Object
    }
  }
}
</script>


<style>
  li{
    display: flex;
    margin: 5px 0;
  }
  span{
    flex: 1
  }
  span.icon{
    border: 1px;
    color: white;
    text-align: right;
    font-size: 0.8rem;
    padding: 2px;
    cursor: pointer
  }

</style>