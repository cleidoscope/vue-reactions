<template>
	<div id="vue_reactions">
		<div v-for="emoji in emojis" :key="emoji.alt" @mouseover="emoji.hovered = true" :title="emoji.name" @mouseout="emoji.hovered = false" class="vue_reaction_content" @click="emit('input', emoji.emoji)">
			<img :src="emoji.hovered ? emoji.gif : emoji.png" :alt="emoji.name" class="vue_reaction" :class="{ vue_reaction_png: !emoji.hovered }" />
		</div>
	</div>
</template>

<script>
import { ref } from 'vue';
import Smile from '/gifs/smile';
import Angry from '/gifs/angry';
import Heart from '/gifs/heart';
import Laugh from '/gifs/laugh';
import Sad from '/gifs/sad';
import Like from '/gifs/like';

export default {
	emits: ['input'],
	setup(props, { emit }) {
		const emojis = ref([
			{
				...Smile,
				...{ hovered: false }
			},
			{
				...Angry,
				...{ hovered: false }
			},
			{
				...Heart,
				...{ hovered: false }
			},
			{
				...Laugh,
				...{ hovered: false }
			},
			{
				...Sad,
				...{ hovered: false }
			},
			{
				...Like,
				...{ hovered: false }
			}
		]);
		return { emojis, emit };
	}
};
</script>

<style scoped>
#vue_reactions {
	display: inline-flex;
	vertical-align: middle;
	align-items: center;
	border: solid 1px #ccc;
	border-radius: 50px;
	overflow: hidden;
}
.vue_reaction {
	width: 40px;
	height: auto;
	pointer-events: none;
	display: inline-block;
	vertical-align: middle;
	transition: filter 0.15s;
}
.vue_reaction_png {
	width: 30px;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	filter: grayscale(0.4);
}
.vue_reaction_content {
	overflow: hidden;
	width: 40px;
	position: relative;
	height: 40px;
	cursor: pointer;
}
</style>
