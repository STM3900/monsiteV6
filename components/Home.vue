<template>
    <div>
        <article>
            <h1>Théo Migeat</h1>
            <h2>Étudiant et alternant en informatique !</h2>
            <section>
                <a @mouseover="changeLabel('Linkedin')" href="https://www.linkedin.com/in/theo-migeat/" target="_blank"><font-awesome-icon class="icon" :icon="['fab', 'linkedin-in']"/></a>
                <a @mouseover="changeLabel('Github')" href="https://github.com/STM3900" target="_blank"><font-awesome-icon class="icon" :icon="['fab', 'github']"/></a>
                <a @mouseover="changeLabel('Mail')" href="mailto:theo.migeat@epsi.fr" target="_blank"><font-awesome-icon class="icon" :icon="['fas', 'envelope']"/></a>
                <a @mouseover="changeLabel('Voir mon CV')" href="" target="_blank"><font-awesome-icon class="icon" :icon="['fas', 'file']"/></a>
                <p>{{ iconText }}</p>
            </section>
        </article>
        <aside>
            <Particles class="particle"
                id="tsparticles"
                :options="{
                        fpsLimit: 60,
                        interactivity: {
                            detectsOn: 'canvas',
                            events: {
                                onHover: {
                                    enable: true,
                                    mode: 'repulse'
                                },
                                resize: true
                            },
                            modes: {
                                repulse: {
                                    distance: 100,
                                    duration: 0.4
                                }
                            }
                        },
                        particles: {
                            color: {
                                value: '#ffffff'
                            },
                            links: {
                                color: '#ffffff',
                                distance: 100,
                                enable: true,
                                opacity: 0.5,
                                width: 1
                            },
                            collisions: {
                                enable: true
                            },
                            move: {
                                direction: 'right',
                                enable: true,
                                outMode: 'out',
                                random: true,
                                speed: 0.2,
                                straight: false
                            },
                            number: {
                                density: {
                                    enable: true,
                                    value_area: 800
                                },
                                value: 20
                            },
                            opacity: {
                                value: 0.8
                            },
                            shape: {
                                type: 'circle'
                            },
                            size: {
                                random: true,
                                value: 5
                            }
                        },
                        detectRetina: true
                    }"
                />
        </aside>
    </div>
</template>

<script>
export default {
    name: 'Home',
    data: function () {
        return {
            iconText: 'slt'
        }
    },
    methods: {
        changeLabel(label){
            this.iconText = label;
        }
    }
}
</script>

<style scoped>
    aside{
        position: absolute;
        height: 100vh;
        width: 100%;
    }

    aside .particle{
        animation-duration: 1s;
        animation-name: fade;
        animation-timing-function: ease;
    }

    div{
        height: 100vh;
        width: 100%;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        align-content: center;

        color: #0CAADC;
        background:#001021;
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
        z-index: 10;

        background: #00102171;
        border-radius: 25px;
    }

    h1{
        font-size: 10rem;
        text-transform: uppercase;
        margin-top: 0;
        margin-bottom: 0;
        font-weight: 500;
    }

    h2{
        font-size: 2.5rem;
        font-weight: normal;
        color: white;
    }

    p{
        transition: 0.3s;
        opacity: 0;
        margin-top: 1rem;
        font-size: 2.5rem;
        color: white;

        
    }

    a:hover ~ p{
        opacity: 1;
    }

    section{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        align-content: center;
        flex-wrap: wrap;

        width: 350px;
        overflow: hidden;
    }

    section a{
        transition: 0.3s;
        color: #0CAADC;
        width: 25%;

        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        align-content: center;
    }

    section a:hover{
        color: rgb(220, 220, 220);
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