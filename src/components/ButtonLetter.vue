<template>
    <v-btn fab dark :id="letra" :style="{ backgroundColor: color }">
      {{letra}}
    </v-btn>
</template>

<script>
export default {
    props:["letra", "color"],
    // data: () => ({
    //     activeColor:'purple'
    // }),
    //    methods : {
    //        add(){
    //            this.idfornitore++; // mutating props directly will result in vuejs warning. i have used this code here to show how this works.
    //            this.$emit("changevalue",this.idfornitore); //cascade the update to parent
    //        }
    //    }
    }
</script>