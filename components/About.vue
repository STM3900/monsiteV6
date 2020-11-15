<template>
    <div>
        <aside>
            <img class="nuage1" src="~/assets/nuage1.png" />
            <img class="nuage2" src="~/assets/nuage2.png" />
        </aside>
        <p>Étudiant en troisième année, à l'Epsi Grenoble, école d'informatique, je suis passionné par le web, où je prends plaisir à concevoir et réaliser des sites internet avec de plus en plus de fonctionnalités !</p>
    </div>
</template>

<script>
export default {
    name: 'About'
}
</script>

<style scoped>
    div{
        height: 50vh;
        width: 100%;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        align-content: center;

        color: white;
        background-image: linear-gradient(to bottom, #001021, #021223, #031425, #051527, #061729);
    }

    aside{
        position: absolute;
        height: 50vh;
        width: 100%;
    }

    .nuage1{
        position: absolute;
        top: 50%;
        right: 4%;
        animation-name: cloud2;
        animation-duration: 10s;
        animation-iteration-count: infinite;
        overflow: hidden;
    }

    .nuage2{
        position: absolute;
        top: 25%;
        left: 7%;
        animation-name: cloud;
        animation-duration: 10s;
        animation-iteration-count: infinite;
        overflow: hidden;
        filter: brightness(0.9);
    }

    p{
        z-index: 10;
        font-size: 2.5rem;
        text-align: center;
        width: 50%;
    }

    @keyframes cloud{
        0% {
        transform: translateX(0px);
        }

        50%{
            transform: translateX(-25px);
        }

        100%{
            transform: translateX(0px);
        }
    }

    @keyframes cloud2{
        0% {
        transform: translateX(0px);
        }

        50%{
            transform: translateX(25px);
        }

        100%{
            transform: translateX(0px);
        }
    }
</style>