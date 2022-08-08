<script setup>
import spin from "./components/spin.vue";
</script>
<script>
export default {
    components: { spin },
    data() {
        return {
            items: [
                {
                    content: "",
                    id: this.generateId(),
                },
            ],
            showSpin: false,
        };
    },
    methods: {
		close(){
			console.log('batya')
		},
        generateId() {
            return new Date().getTime().toString(36);
        },
        addItem() {
            this.items.push({
                content: "",
                id: this.generateId(),
            });
        },
        removeItem(id) {
            this.items = this.items.filter((item) => {
                let result = item.id === id;
                return !result;
            });
        },
    },
};
</script>

<template>
    <div class="container">
        <div class="inputs_wrapper">
            <div class="input_box">
                <div v-for="item in items" :key="item.id" class="input_item">
                    <div class="remove_wrapper">
                        <div
                            class="input_remove"
                            v-if="items.length > 1"
                            @click="removeItem(item.id)"
                        >
                            <span>+</span>
                        </div>
                    </div>
                    <input type="text" v-model="item.content" />
                </div>
            	<div class="input_button" @click="addItem">+</div>
            </div>
			<div class="run_random">
				<div class="start_button" @click="showSpin = true">Start</div>
			</div>
        </div>
		<spin :list="items" v-show="showSpin" v-model="showSpin"/>
    </div>
</template>

<style lang="scss">
.container{
	display: flex;
	justify-content: space-around;
	align-items: center;
	width: 90%;
	max-width: 800px;
	& > *{
		width: 50%;
	}
}
.inputs_wrapper {
	display: flex;
	flex-direction: column;
	align-items: center;
}
.input_box {
	position: relative;
    .input_item {
        position: relative;
        .remove_wrapper {
            position: absolute;
            top: 0;
            left: -25px;
            width: 50px;
            height: 50px;
        }
        .input_remove {
            position: absolute;
            top: 5px;
            left: -7px;
            border: 2px solid #fff;
            cursor: pointer;
            width: 25px;
            height: 25px;
            color: #fff;
            display: none;
            justify-content: center;
            align-items: center;
            transition: all 0.2s ease;
            font-size: 20px;
            border-radius: 7px;
            span {
                transform: rotate(45deg);
            }
            &:hover {
                background-color: #fff;
                color: #383838;
            }
        }
        &:hover {
            .input_remove {
                display: flex;
            }
        }
    }
    input {
        display: block;
        border: none;
        border: 2px solid #fff;
        background: transparent;
        border-radius: 4px;
        height: 36px;
        width: 200px;
        padding: 5px 10px;
        color: #fff;
        margin-top: 5px;
        &:first-child {
            margin-top: 0;
        }
    }
}
.input_button {
    position: absolute;
    top: 5px;
    right: -32px;
    border: 2px solid #fff;
    width: 25px;
    height: 25px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    border-radius: 7px;
    cursor: pointer;
    transition: all 0.2s ease;
    font-weight: 700;
    font-size: 20px;
    &:hover {
        background-color: #fff;
        color: #383838;
    }
}
.run_random {
    margin-top: 10px;
    display: flex;
    justify-content: center;
    .start_button {
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
}
</style>
