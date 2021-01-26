<script>
	export let song;
</script>

<main>
	<div class="song">
		<div class="innerSong">
			<div class="imageHolder">
				<img src={song["im:image"][2].label} alt="Avatar">
			</div>
			<div class="details">
				<h1>{song["im:name"].label}</h1><br>
				<p><b>By: </b>{song["im:artist"].label}</p>
			</div>
		</div>
	</div>
</main>

<style>
		/* The flip card container - set the width and height to whatever you want. We have added the border property to demonstrate that the flip itself goes out of the box on hover (remove perspective if you don't want the 3D effect */
	.song {
		background-color: transparent;
		width: 250px;
		height: 250px;
		perspective: 1000px; /*Remove this if you don't want the 3D effect */
		margin: 10px;
	}

	/* This container is needed to position the front and back side */
	.innerSong {
		position: relative;
		width: 100%;
		height: 100%;
		text-align: center;
		transition: transform 0.8s;
		transform-style: preserve-3d;
	}

	/* Do an horizontal flip when you move the mouse over the flip box container */
	.song:hover .innerSong {
		transform: rotateY(180deg);
	}

	/* Position the front and back side */
	.imageHolder, .details {
		position: absolute;
		width: 100%;
		height: 100%;
		-webkit-backface-visibility: hidden; /* Safari */
		backface-visibility: hidden;
	}

	/* Style the front side (fallback if image is missing) */
	.imageHolder {
		background-color: #bbb;
		color: black;
	}

	/* Style the back side */
	.details {
		background-color: #ff5690;
		color: white;
		transform: rotateY(180deg);
		padding: 20px;
	}
	img{
		height: 250px;
	}
</style>
