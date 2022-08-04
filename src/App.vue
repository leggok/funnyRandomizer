<script>
export default {
    methods: {
        addItem: function () {
            console.log('add')
            let newInput = document.createElement("input");
            newInput.setAttribute("type", "text");
            newInput.setAttribute("placeholder", "Input item");

            let newInputItem = document.createElement("div");
            newInputItem.classList.add("input_item");

            let newRemoveWrapper = document.createElement("div");
            newRemoveWrapper.classList.add("remove_wrapper");

            let newInputRemove = document.createElement("div");
            newInputRemove.classList.add("input_remove");
            console.log(1)
            newInputRemove.setAttribute("@click", "removeItem")
            console.log(2)
            
            newRemoveWrapper.appendChild(newInputRemove)
            
            let newSpan = document.createElement('span');
            newSpan.innerHTML = '+';

            newInputRemove.appendChild(newSpan);

            newInputItem.appendChild(newRemoveWrapper)
            newInputItem.appendChild(newInput)
            document.querySelector(".input_box").appendChild(newInputItem);
        },

        removeItem: function (e) {
            console.log('remove')
            e.target.parentElement.remove();
        },
    },
};
</script>

<template>
    <div class="container">
        <div class="inputs_wrapper">
            <div class="input_box">
                <div class="input_item">
                    <div class="remove_wrapper">
                        <div class="input_remove" @click="removeItem">
                            <span>+</span>
                        </div>
                    </div>
                    <input type="text" placeholder="Input item" />
                </div>
            </div>
            <div class="input_button" @click="addItem">+</div>
        </div>
        <div class="run_random">
            <div class="start_button">Start</div>
        </div>
    </div>
</template>

<style lang="scss">
.inputs_wrapper {
    position: relative;
}
.input_box {
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
