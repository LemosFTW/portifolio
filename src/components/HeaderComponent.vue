<template>
    <div class="header-wrapper">
        <!-- Botão de toggle -->
        <button class="toggle-button" @click="toggleMenu" :class="{ 'open': isMenuOpen }">
            <span></span>
            <span></span>
            <span></span>
        </button>

        <!-- Container principal com classe dinâmica -->
        <div class="container" :class="{ 'menu-open': isMenuOpen }">
            <div v-for="field in fields" :key="field.title">
                <h1 @click="$emit('section-click', field.title)">{{ field.title }}</h1>
            </div>

            <div v-for="icon in icons" :key="icon.title">
                <component :is="icon.imageUrl" class="iconLink" @click="$emit('icon-click', icon.url)"/>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'HeaderComponent',
    props: {
        fields: Array,
        icons: Array
    },
    data() {
        return {
            isMenuOpen: false
        }
    },
    methods: {
        toggleMenu() {
            this.isMenuOpen = !this.isMenuOpen;
        }
    }
}
</script>
<style scoped>
.container {
    display: flex;
    flex-direction: row;
    background-color: #1B1B1B;
    justify-content: space-around;
    border-radius: 10px;

}

.container h1 {
    color: #9C9C9C;
    font-size: 14px;
}

.container h1:hover {
    color: #FFFFFF;
    font-size: 14px;
}
.container img{
    width: 20px;
    height: 20px;
}
.iconLink{
    background-color: transparent;
    width: 20px;
    height: 20px;
    display: block;
    padding: 10px;
}

.container > div {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
    padding: 0 10px;
}
@media screen and (max-width: 768px) {
    .container {
        flex-direction: column;
        align-items: center;
        gap: 10px;
    }

    .container > div {
        padding: 5px;
    }

    .container h1 {
        font-size: 12px;
    }

    .iconLink {
        padding: 5px;
    }
}

@media screen and (max-width: 480px) {
    .container {
        padding: 5px;
    }

    .container h1 {
        font-size: 10px;
    }

    .iconLink {
        width: 15px;
        height: 15px;
    }
}

.header-wrapper {
    position: relative;
}

.toggle-button {
    display: none;
    flex-direction: column;
    justify-content: space-between;
    width: 30px;
    height: 21px;
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 0;
    position: absolute;
    right: 20px;
    top: 20px;
    z-index: 2;
}

.toggle-button span {
    width: 100%;
    height: 3px;
    background-color: #fff;
    transition: all 0.3s ease;
}

.toggle-button.open span:first-child {
    transform: rotate(45deg) translate(6px, 6px);
}

.toggle-button.open span:nth-child(2) {
    opacity: 0;
}

.toggle-button.open span:last-child {
    transform: rotate(-45deg) translate(6px, -6px);
}

@media screen and (max-width: 768px) {
    .toggle-button {
        display: flex;
    }

    .container {
        display: none;
        width: 100%;
    }

    .container.menu-open {
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 10px;
        padding-top: 60px;
    }
}

</style>

