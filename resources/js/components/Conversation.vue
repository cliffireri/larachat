<template>
  <div class="conversation">
      <h1>{{  contact?contact.name:'Select a contact' }}</h1>
      <MessageFeed :contact="contact" :messages="messages"/>
      <MessageComposer @send="sendMessage" />
  </div>
</template>

<script>
import MessageFeed from './MessageFeed'
import MessageComposer from './MessageComposer'
export default {
    props: {
        contact: {
            type: Object,
            default: null
        },
        messages: {
            type: Array,
            default:[]
        }
    },
    components: {
        MessageComposer,MessageFeed
    },
    methods: {
        sendMessage(text){
            console.log(text)
        }
    },
    name: 'conversation',
}
</script>

<style>

</style>