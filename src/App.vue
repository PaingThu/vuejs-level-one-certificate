<script setup>
import { items } from "./movies.json";

/*
 This is an Icon that you can use to represent the stars if you like
 otherwise you could just use a simple ⭐️ emoji, or * character.
*/
import { StarIcon } from "@heroicons/vue/24/solid";
import { reactive } from "vue";

const movies = reactive(items)
</script>

<template>
    <!-- This is where your template goes	-->
    <div class="app">
        <div class="movie-list">
            <div class="movie-item" v-for="(movie, index) in items" :key="index">
                <div class="image-wrapper">
                    <img :src="movie.image" alt="">
                </div>
                <div class="content-wrapper">
                    <div class="title-wrapper">
                        <h3 class="title">{{ movie.name }}</h3>
                        <div class="genres-wrapper">
                            <span class="genre-tag" v-for="genre in movie.genres" :key="`${movie.id}-${genre}`">
                                {{ genre }}
                            </span>
                        </div>
                    </div>
                    <div class="description-wrapper">
                        <p class="description">{{ movie.description }}</p>
                    </div>
                    <div class="rating-wrapper">
                        <span class="rating-text">
                            Rating: ({{ movie.rating }}/5)
                        </span>
                        <StarIcon 
                            v-for="star in movie.rating" 
                            :key="`star-${star}`"
                            class="star-icon"
                        />
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
