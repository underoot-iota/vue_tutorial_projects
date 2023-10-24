<template>
    <h1>{{ title }}</h1>
    <!-- <input type="text" ref="name">
    <button @click="handleClick()">Click Me :0</button> -->

    <p>Welcome...</p>

    <div v-if="showModal">
        <!-- <Modal :header="header" :content="content" theme="dark" @close="toggleModal()"/> -->

        <!-- SLOTS - instead of self closing modal tag, we write specific open and close tags -->
        <Modal
            :header="header"
            :content="content"
            theme="dark"
            @close="toggleModal()"
        >
            <template v-slot:links>
                <a href="#">Sign Up</a>
                <a href="#">More Info</a>
            </template>
        </Modal>
    </div>
    <!-- CLICK EVENT MODIFIER -->
    <button @click.alt="toggleModal()">Toggle Modal 1 (alt)</button>

    <br />
    <br />

    <!-- 2nd Modal teleporting to DIV with class '.modals' -->

    <Teleport to=".modals" v-if="showModal2">
        <Modal
            :header="header"
            :content="content2"
            :theme="dark"
            @close="toggleModal2()"
        >
            <template v-slot:info>
                <p>Name - Shantanu</p>
                <p>Age - 20</p>
                <p>College - IIITA</p>
            </template>
        </Modal>
    </Teleport>
    <button @click.right="toggleModal2()">Toggle Modal 2 (right)</button>
</template>





<script>
import Modal from "./components/Modal.vue";

export default {
    name: "App",
    components: { Modal },

    data() {
        return {
            title: "My First Vue App :)",
            header: "My name is underoot_iota",
            content: "real name is Shantanu",
            showModal: false,
            showModal2: false,
            content2: "Hello",
        };
    },

    methods: {
        toggleModal() {
            this.showModal = !this.showModal;
        },
        toggleModal2() {
            this.showModal2 = !this.showModal2;
        },
    },

    //   methods: {

    //     handleClick() {
    //         console.log(this.$refs.name)
    //         this.$refs.name.classList.add('active')
    //         this.$refs.name.focus()
    //     }

    //   }
};
</script>





<style>
#app, .modals {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
