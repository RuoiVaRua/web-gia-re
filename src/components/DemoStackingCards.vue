<template>
	<div class="container">
        <ul id="cards">
            <li class="card" id="card1">
                <div class="card-body">
                    <h2>Card 1</h2>
                </div>
            </li>
            <li class="card" id="card2">
                <div class="card-body">
                    <h2>Card 2</h2>
                </div>
            </li>
            <li class="card" id="card3">
                <div class="card-body">
                    <h2>Card 3</h2>
                </div>
            </li>
            <li class="card" id="card4">
                <div class="card-body">
                    <h2>Card 4</h2>
                </div>
            </li>
        </ul>
    </div>
</template>

<style scoped lang="scss">
$cards: 4;
$cardHeight: 87vh;
$cardTopPadding: 1.5em;
$cardMargin: 4vw;

.container {
	width: 90%;
	margin: 0 auto;
}

#cards {
	list-style: none;
	padding-left: 0;
	display: grid;
	grid-template-columns: 1fr;
	grid-template-rows: repeat($cards, $cardHeight);
	gap: $cardMargin;
	padding-bottom: calc($cards * $cardTopPadding);
	margin-bottom: $cardMargin;
}

#card1 {
	--index: 1;
}
#card2 {
	--index: 2;
}
#card3 {
	--index: 3;
}
#card4 {
	--index: 4;
}

.card {
	position: sticky;
	top: 0;
	padding-top: calc(var(--index) * $cardTopPadding);
}

#card1 .card-body {
	background-color: #52B2CF;
}
#card2 .card-body {
	/* background-color: #7EC4CF; */
	background-color: #E5A36F;
}
#card3 .card-body {
	background-color: #9CADCE;
}
#card4 .card-body {
	background-color: #D4AFB9;
}

.card-body {
	box-sizing: border-box;
	padding: 30px;
	border-radius: 50px;
	box-shadow: 0 0 30px 0 rgba(0,0,0,0.3);
	height: $cardHeight;
	display: flex;
	justify-content: center;
	align-items: center;
	transition: all 0.5s;
}

h2 {
	font-size: 2.5em;
}
</style>