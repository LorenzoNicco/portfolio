<script>
    import { store } from "../store.js"
    export default {
        name: "RoadmapSection",
        data() {
            return {
                store
            }
        },
        props: [
            "data"
        ]
    }
</script>

<template>
    <div class="data-container col p-0 mb-2 mb-lg-5 d-flex flex-column align-items-center justify-content-end">
        <h4 class="company-name" data-bs-toggle="modal" :data-bs-target="'#'+data.id">{{ data.company }}</h4>

        <div class="vertical-line"></div>

        <div class="horizontal-line d-none d-lg-block"></div>

        <div class="time-dot"></div>

        <p v-if="store.language == 'ita'" class="duration-period">{{ data.duration }}</p>
        <p v-if="store.language == 'eng'" class="duration-period">{{ data.durationEng }}</p>

        <!-- Modal -->
        <div class="modal fade" :id="data.id" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog modal-dialog-centered">
                <div class="modal-content">
                    <div class="modal-header">
                        <h2 v-if="store.language == 'ita'" class="modal-title fs-3" id="exampleModalLabel">{{ data.title }}</h2>
                        <h2 v-if="store.language == 'eng'" class="modal-title fs-3" id="exampleModalLabel">{{ data.titleEng }}</h2>
                    </div>

                    <ul class="modal-body list-unstyled ms-5 ps-1">
                        <li>
                            <span class="fa-li"><font-awesome-icon icon="fa-solid fa-building" /></span>
                            <h5>{{ data.company }}</h5>
                        </li>

                        <li>
                            <span class="fa-li"><font-awesome-icon icon="fa-solid fa-map-location-dot" /></span>
                            <p v-if="store.language == 'ita'">{{ data.location }}</p>
                            <p v-if="store.language == 'eng'">{{ data.locationEng }}</p>
                        </li>

                        <li>
                            <span class="fa-li"><font-awesome-icon icon="fa-regular fa-hourglass-half" /></span>
                            <p v-if="store.language == 'ita'">{{ data.duration }}</p>
                            <p v-if="store.language == 'eng'">{{ data.durationEng }}</p>
                        </li>

                        <li>
                            <span class="fa-li"><font-awesome-icon icon="fa-solid fa-circle-question" /></span>
                            <p v-if="store.language == 'ita'">{{ data.description }}</p>
                            <p v-if="store.language == 'eng'">{{ data.descriptionEng }}</p>
                        </li>
                    </ul>

                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .data-container {
        .company-name {
            cursor: pointer;
            text-align: center;
            padding: 0 1rem;
            transition: 0.2s ease-in;
        }


        .company-name:hover {
            color: orange;
        }

        .vertical-line {
            width: 10px;
            height: 30px;
            background-color: cornflowerblue;
            border-top-left-radius: 5px;
            border-top-right-radius: 5px;
        }
    
        .horizontal-line {
            width: 100%;
            height: 10px;
            background-color: cornflowerblue;
        }
    
        .time-dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            margin: 10px 0;
            background-color: cornflowerblue;
        }
    
        .duration-period {
            text-align: center;
            font-size: 0.7rem;
        }
    }

    // Fine timeline
    .data-container:last-child > .horizontal-line {
        position: relative;
    }
    
    .data-container:last-child > .horizontal-line::after {
        content: '';
        position: absolute;
        top: 0;
        right: -10px;
        height: 10px;
        width: 10px;
        background: linear-gradient(135deg, cornflowerblue 50%, rgba(255,255,255,1) 50%);;
    }

    // Inizio timeline
    .data-container:first-child > .horizontal-line {
        position: relative;
    }
    
    .data-container:first-child > .horizontal-line::before {
        content: '';
        position: absolute;
        top: 0;
        left: 5px;
        height: 10px;
        width: 5px;
        background: white;
    }

    // modal
    .modal-header {
        background-color: orange;
    }
</style>