<script>
export default {
    props: ["list", "showSpin"],
    data() {
        return {
            result: "",
        };
    },
    methods: {
        random() {
            this.result =
                this.list[Math.floor(Math.random() * this.list.length)].content;
        },
        close(){
            this.$emit('showSpin', false);
        }
    },
};
</script>
<template>
    <div class="spinner">
        <div class="remove_wrapper">
            <div
                class="input_remove"
                @click="this.close"
            >
                <span>+</span>
            </div>
        </div>
        <ul>
            <li v-for="li in list" :key="li.id">{{ li.content }}</li>
        </ul>
        <div class="result">{{ this.result }}</div>
        <div class="spin_button" :method="close" @click="this.random()">Spin</div>
    </div>
</template>

<style lang="scss">
.result{
    color: #fff;
}
.spinner{
    position: absolute;
    left: 0;
    top: 0;
    width: 100% !important;
    max-width: initial;
    height: 100%;
    background: #000;
}
ul {
    list-style: none;
    border: 2px solid #fff;
    border-radius: 10px;
    padding: 5px;
    li {
        color: #fff;
        border-bottom: 1px solid #606060;
    }
}
.spin_button {
    margin: 10px 0;
    color: #383838;
    border: 1px solid transparent;
    background: #fff;
    border-radius: 6px;
    padding: 6px 17px;
    font-size: 18px;
    cursor: pointer;
    transition: all 0.2s ease;
    &:hover {
        color: #fff;
        background: #383838;
        border-color: #fff;
    }
}
</style>