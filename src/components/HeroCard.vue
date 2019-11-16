<template>
    <div class="hero-card">
        <h2>{{name}}</h2>
        <img :src="img" alt="Hero image"/>
    </div>
</template>

<script>
export default {
    name: "HeroCard",
    props: {
        name: String,
        img: String 
    }
}
</script>

<style scoped>
    .hero-card {
        margin: 35px;
        text-align: center;
        transition: all 500ms ease;
        border: 1px solid black;
    }
    
    .hero-card:hover {
        -webkit-transform: scale(1.1);
        -ms-transform: scale(1.1);
        transform: scale(1.1);
    }

    img {
        margin: 0 10px 0 10px;
    }

    @keyframes bounce {
	0%, 20%, 60%, 100% {
		-webkit-transform: translateY(0);
		transform: translateY(0);
	}

	40% {
		-webkit-transform: translateY(-20px);
		transform: translateY(-20px);
	}

	80% {
		-webkit-transform: translateY(-10px);
		transform: translateY(-10px);
	}
}
</style>