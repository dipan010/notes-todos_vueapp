<template>
    <div class="col-md-3 col-sm-4 col-xs-6">
        <div class="note-element">
            <span class="note-title"> {{todo.title}} </span>
            <span class="icon" @click.prevent="$emit('remove', todo)"> <img src="https://img.icons8.com/metro/15/000000/cancel.png"/> </span>
            <div class="note-body"> {{todo.text}} </div>
        </div>
    </div>
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
  span{
    flex: 1;
  }
  span.icon
  { border: 1px;  
    color: white;
    text-align: right;
    font-size: 0.8rem;
    padding: 2px;
    cursor: pointer;
  }

</style>