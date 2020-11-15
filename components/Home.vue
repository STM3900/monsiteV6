<template>
    <div>
        <article>
            <h1>Théo Migeat</h1>
            <h2>Étudiant et alternant en informatique !</h2>
            <section>
                <a href="https://www.linkedin.com/in/theo-migeat/" target="_blank"><font-awesome-icon class="icon" :icon="['fab', 'linkedin-in']"/></a>
                <a href="https://github.com/STM3900" target="_blank"><font-awesome-icon class="icon" :icon="['fab', 'github']"/></a>
                <a href="mailto:theo.migeat@epsi.fr" target="_blank"><font-awesome-icon class="icon" :icon="['fas', 'envelope']"/></a>
                <a href="" target="_blank"><font-awesome-icon class="icon" :icon="['fas', 'file']"/></a>
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
                                distance: 50,
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
                                speed: 0.1,
                                straight: false
                            },
                            number: {
                                density: {
                                    enable: true,
                                    value_area: 800
                                },
                                value: 40
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
    name: 'Home'
}
</script>

<style scoped>
    aside{
        position: absolute;
        height: 100vh;
        width: 100vw;

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

    section{
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        align-content: center;
    }

    section a{
        transition: 0.3s;
        color: #0CAADC;
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