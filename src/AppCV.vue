<template>
     <div class="card card-w70">
        <div v-if="blockInfo.length">
          <component 
          v-for="block in blockInfo"
          :key="block.id"
          :is="'resume-' + block.type"
          v-bind="{value: block.value}">
          </component>

          
        </div>
        <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
   
    </div>
</template>

<script>
import ResumeTitle from "./ResumeComps/ResumeTitle.vue"
import ResumeText from "./ResumeComps/ResumeText.vue"
import ResumeAvatar from "./ResumeComps/ResumeAvatar.vue"
import ResumeSubtitle from "./ResumeComps/ResumeSubtitle.vue"
export default {
    props: ['blockInfo'],
    components: {ResumeTitle, ResumeText, ResumeAvatar, ResumeSubtitle}


   

}
</script>

<style>

</style>