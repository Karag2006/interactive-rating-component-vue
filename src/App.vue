<script setup>
    import { ref, computed } from "vue";

    const rating = ref("#");
    const displayResult = ref(false);
    const thanksClass = ref("");
    const resultHeadline = ref("Thank you!");
    const resultText =
        ref(`We appreciate you taking the time to give a rating. If you ever
                need more support, don’t hesitate to get in touch!`);
    const ratingResult = computed(() => {
        if (rating.value == "#") {
            return "That was wrong";
        }
        return `You selected ${rating.value} out of 5`;
    });

    const resultClass = ref("");

    const showResult = function () {
        if (rating.value == "#") {
            resultHeadline.value = "Are you stupid?";
            resultText.value =
                "Choosing a rating value is not that hard - just click on a number before submiting.";
            thanksClass.value = "animation-sad";
        } else {
            thanksClass.value = "animation";
        }
        displayResult.value = true;
        resultClass.value = "visible";
    };
</script>

<template>
    <main>
        <div
            id="result"
            :class="`rating flex-flow ${resultClass}`"
            v-if="displayResult"
        >
            <div class="rating--thanks" :class="thanksClass"></div>
            <p class="rating--result">{{ ratingResult }}</p>
            <h2 id="headline" class="rating--headline">{{ resultHeadline }}</h2>
            <p id="text" class="rating--text">
                {{ resultText }}
            </p>
        </div>

        <div id="vote" class="rating animation-item flex-flow" v-else>
            <div class="rating--star animation-item"></div>
            <h2 class="rating--headline animation-item">How did we do?</h2>
            <p class="rating--text animation-item">
                Please let us know how we did with your support request. All
                feedback is appreciated to help us improve our offering!
            </p>
            <div class="rating--score animation-item grid-flow">
                <button
                    :class="rating == 1 ? 'active' : ''"
                    class="score animation-item grid-flow"
                    @click="rating = 1"
                >
                    1
                </button>
                <button
                    :class="rating == 2 ? 'active' : ''"
                    class="score animation-item grid-flow"
                    @click="rating = 2"
                >
                    2
                </button>
                <button
                    :class="rating == 3 ? 'active' : ''"
                    class="score animation-item grid-flow"
                    @click="rating = 3"
                >
                    3
                </button>
                <button
                    :class="rating == 4 ? 'active' : ''"
                    class="score animation-item grid-flow"
                    @click="rating = 4"
                >
                    4
                </button>
                <button
                    :class="rating == 5 ? 'active' : ''"
                    class="score animation-item grid-flow"
                    @click="rating = 5"
                >
                    5
                </button>
            </div>
            <button
                id="submit-button"
                class="button animation-item"
                @click="showResult()"
            >
                Submit
            </button>
        </div>

        <div class="attribution">
            Challenge by
            <a
                href="https://www.frontendmentor.io?ref=challenge"
                target="_blank"
                >Frontend Mentor</a
            >. Coded by
            <a href="https://github.com/gnss85/">Patrick Richter</a>.
        </div>
    </main>
</template>

<style lang="scss" scoped></style>
