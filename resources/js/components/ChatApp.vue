<template>
    <div class="chat-app">
        <Conversation :contact="selectedContact" :messages="messages"/>
        <ContactList :contacts="contacts" @selected="startConversationWith"/>
    </div>
</template>

<script>
    import Conversation from './Conversation'
    import ContactList from './ContactList'

    export default {
        props: {
            user: {
                type:Object,
                required:true
            }
        },
        data(){
            return {
                selectedContact: null,
                messages: [],
                contacts: []
            }
        },
        methods: {
            startConversationWith(contact){
                axios.get(`/conversations/${contact.id}`).then(response => {
                    this.messages = response.data
                    this.selectedContact = contact
                })
            }
        },
        mounted() {
            console.log(this.user)
            axios.get('/contacts').then((response) => {
                console.log(response.data)
                this.contacts = response.data
            })
        },
        components: {
            Conversation,ContactList
        }
    }
</script>
