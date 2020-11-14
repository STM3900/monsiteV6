<template>
    <div>
        <article>
            <h1>Théo Migeat</h1>
            <h2>Étudiant et alternant en informatique !</h2>
            <section>
                <font-awesome-icon class="icon" :icon="['fab', 'linkedin-in']"/>
                <font-awesome-icon class="icon" :icon="['fab', 'github']"/>
                <font-awesome-icon class="icon" :icon="['fas', 'envelope']"/>
                <font-awesome-icon class="icon" :icon="['fas', 'file']"/>
            </section>
        </article>
    </div>
</template>

<script>
export default {
    name: 'Home'
}
</script>

<style scoped>
    div{
        height: 100vh;
        width: 100%;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        align-content: center;

        background: #001021;
        color: #0CAADC;
    }

    article{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        align-content: center;

        animation-duration: 1s;
        animation-name: fade;
        animation-timing-function: ease;
    }

    h1{
        font-size: 10rem;
        text-transform: uppercase;
        margin-top: 0;
        margin-bottom: 0;
    }

    h2{
        font-size: 2.5rem;
        font-weight: normal;
        color: white;
    }

    section{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        align-content: center;
    }

    section .icon{
        font-size: 4rem;
        margin-top: 2rem;
        margin-right: 2rem;
        margin-left: 2rem;
    }

    @keyframes fade {
        from {
            opacity: 0;
            transform: scale(0.98);
        }

        to {
            opacity: 1;
            transform: scale(1);
        }
    }
</style>