<script lang="ts">

function newWord(): string{
	let possibleWords: string[] = ["Improfessional","Hobbyist","Newbie","Young"];
	let chosenWordArray = Math.floor(Math.random() * 4);
	let chosenWord = possibleWords[chosenWordArray]
	return chosenWord;
}

</script>
<div class="px-20 py-15">
	<h1 class="text-[6rem] font-bold text-[#cdd6f4]">Adrian Tennies</h1>

	<p class="px-5 py-3 text-[3rem] font-semibold text-[#bac2de]">
		{newWord()} Software Developer
	</p>
</div>
