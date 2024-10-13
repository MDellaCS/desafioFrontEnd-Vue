<template>

    <div class="user-card">

        <div class="switch-container">
            <button @click="setYellowCard" class="yellow-button"></button>
            <button @click="setRedCard" class="red-button"></button>
        </div>

        <div class="colored-background" :style="{ backgroundColor: cardColor }">

            <div class="image-preview" :style="{ backgroundColor: cardColor, borderColor: borderColor }">

                <img v-if="userImage" :src="userImage" />

                <p v-else></p>

            </div>

            <div class="fullname">

                <p class="name">{{ userName }}</p>
                &nbsp;
                <p class="surname" :style="{ color: cardColor }">{{ userSurname }}</p>

            </div>

        </div>

    </div>
</template>

<script>
export default {
    props: {
        userImage: {
            type: String,
            default: null,
        },
        userName: {
            type: String,
            default: '',
        },
        userSurname: {
            type: String,
            default: '',
        },
    },
    data() {
        return {
            cardColor: '#ecb117',
            borderColor: '#000',
        };
    },
    methods: {
        setYellowCard() {
            this.cardColor = '#ecb117';
            this.borderColor = '#000';
        },
        setRedCard() {
            this.cardColor = '#9b0021';
            this.borderColor = '#fff';
        },
    },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');

.colored-background {
    padding: 3rem;

    position: relative;
}

.user-card {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;
    gap: 1rem;
}

.image-preview {
    width: 200px;
    height: 200px;
    border: solid 3px #000;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
}

.image-preview img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

p {
    font-family: 'Roboto', sans-serif;
    font-size: .9rem;
    font-weight: 500;
}

.fullname {
    position: absolute;
    bottom: 0;
    transform: translateY(105%);
    left: 0;

    background-color: #000;
    width: 100%;
    height: 15%;
    display: flex;
    align-items: center;
    justify-content: center;

    overflow: hidden;
}

.fullname>.name {
    color: #ffffff;
}

.button-container {
    display: flex;
    justify-content: space-between;
    width: 100%;
    margin-top: 10px;
}

button {
    width: 45%;
    padding: 0.5rem;
    border: none;
    cursor: pointer;
    font-family: 'Roboto', sans-serif;
    font-weight: 500;
}

.yellow-button {
    width: 35px;
    height: 35px;
    border: solid 3px #cccccc;
    background-color: #ecb117;
}

.red-button {
    width: 35px;
    height: 35px;
    border: solid 3px #cccccc;
    background-color: #9b0021;
}

.switch-container {
    display: flex;
    flex-direction: row;
    gap: 1rem;
}
</style>