<template>
    <form @submit.prevent="submitForm">

        <div class="image-container">

            <div class="image-preview">

                <img v-if="formData.image" :src="formData.image" />

                <p v-else></p>

            </div>

            <label for="btnImage">ADICIONAR FOTO</label>
            <input type="file" id="btnImage" @change="onFileChange" />

        </div>

        <div class="fullname-container">

            <div>

                <label for="name">Nome</label>
                <input type="text" v-model="formData.name" id="name" @input="emitInputChange" />

            </div>

            <div>

                <label for="surname">Sobrenome</label>
                <input type="text" v-model="formData.surname" id="surname" @input="emitInputChange" />

            </div>

        </div>

    </form>
</template>

<script>
export default {
    data() {
        return {
            formData: {
                image: null,
                name: '',
                surname: '',
            },
        };
    },
    methods: {
        emitInputChange() {
            this.$emit('input-changed', this.formData);
        },
        onFileChange(event) {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = (e) => {
                    this.formData.image = e.target.result;
                    this.emitInputChange();
                };
                reader.readAsDataURL(file);
            }
        },
    },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');

form {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    justify-content: flex-start;

    width: 600px;
    gap: 1rem;
}

.image-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.image-preview {
    width: 200px;
    height: 200px;
    border: solid 1px #000;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    background-color: white;
}

.image-preview img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

input[type="file"] {
    display: none;
}

.image-container label {
    width: 75%;
    text-align: center;
    margin-top: 10px;
    padding: .5rem 1rem;
    background-color: #FF9900;
    color: white;
    border: none;
    cursor: pointer;

    font-family: 'Roboto', sans-serif;
    font-size: .9rem;
    font-weight: 500;
}

.fullname-container {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-start;
    gap: 1rem;
}

.fullname-container>div {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-start;
    gap: .5rem;
}

.fullname-container label {
    font-family: 'Roboto', sans-serif;
    font-size: .9rem;
    font-weight: 500;
}

.fullname-container input {
    padding: .6rem .3rem;
    border: solid 1px #cccccc;

    font-family: 'Roboto', sans-serif;
    font-size: .9rem;
    font-weight: 500;
}

@media(max-width: 720px) {
    form {
        width: 100%;
        flex-direction: column;
        align-items: center;
        gap: 2rem;
    }
}
</style>