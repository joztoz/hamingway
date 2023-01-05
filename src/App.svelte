<script>
// imports
import { circOut, cubicOut } from 'svelte/easing'
import { shuffleArray } from './functions'
import { tweened } from 'svelte/motion'

// components
import TheBook from './components/TheBook.svelte'
import Wave from './components/Wave.svelte'


// vars
let waving = true
let animationEnded = false
let bookHasBeenRead = false

let books = localStorage.getStuff('unreadBooks')
let audio = new Audio('./assets/dsshotgn.wav')

// countdown
const progress = tweened(0, {
	duration: 2500,
	easing: circOut
})

// func
const chooseBook = () => {
	books = localStorage.getStuff('unreadBooks')
	shuffleArray(books)

	console.log(books)

	animationEnded = false
	bookHasBeenRead = false

	let index = $progress === 0 ? books.length -1 : 0
	progress.set(index).then(() => {
			animationEnded = true
			audio.play()
		})

}

const readBook = () => {
	let readBooks = localStorage.getStuff('readBooks')
	let unreadBooks = localStorage.getStuff('unreadBooks')

	bookHasBeenRead = true

	readBooks.push(choosenStory)
	unreadBooks = unreadBooks.filter(items => items.id !== choosenStory.id)

	localStorage.setStuff('readBooks', readBooks)
	localStorage.setStuff('unreadBooks', unreadBooks)
}

$: choosenStory = books[Math.floor($progress)] || books[0]

</script>

<style>
	label {
		position: absolute;
		top: 2em;
		left: 1em;
		font-size: 0.7em;
	}


</style>

<header>
	<h1>HEMINGWAYOVÁTORO-ROTÁTOR</h1>

	<label for="waving">
		<input type="checkbox" id="waving" bind:checked={waving}>
		waving
	</label>
</header>

	
<main>

	<!-- svelte-ignore missing-declaration -->
	
	<TheBook {choosenStory} {animationEnded} {bookHasBeenRead}/>
	
	<section class="controls">
		<!-- svelte-ignore a11y-click-events-have-key-events -->
		<img on:click={chooseBook} src="./assets/gun.png" alt="cool ass gun" />
		<!-- svelte-ignore a11y-click-events-have-key-events -->
		<img on:click={readBook} src="./assets/anchor.png" alt="sweet anchor" />
	</section>
</main>

<footer class="water">
	<Wave where="back" animation="big" {waving}/>
	<Wave where="middle" animation="tiny" {waving}/>
	<Wave where="front" animation="small" {waving}/>
	<img src="./assets/hemingway.png" alt="my boy ernest" class="hem">
</footer>