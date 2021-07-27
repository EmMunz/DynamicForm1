<template>
<div>
<v-card-title>Please fill in the form below</v-card-title>
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