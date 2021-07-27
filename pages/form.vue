<template>
<div>
<h1> Form page</h1>
<component :is="form"/>
</div>
</template>
<script>
import form from "~/components/form.vue";
export default{
components: {
    form
},
data(){
    return{
     form
    }
}
}
</script>