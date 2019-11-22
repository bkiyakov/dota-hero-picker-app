<template>
    <div class="hero-card">
        <h2>{{hero.localized_name}}</h2>
        <img :src="'https://api.opendota.com' + hero.img" alt="Hero image"/>
        <ul>
            <li>
                <p v-bind:key="hero.roles.indexOf(role)" v-for="role in hero.roles">{{role}}</p>
            </li>
            <hr>
            <li>{{attr}}</li>
        </ul>
    </div>
</template>

<script>

export default {
    name: "HeroCard",
    props: ["hero"],
    computed: {
        attr: function(){
            switch (this.hero.primary_attr) {
                case "agi":
                    return "Agility";
                case "str":
                    return "Strength";
                case "int":
                    return "Intelligence";
                default:
                    return "Default";
            }
        }
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

    ul {
        text-align: center;
        padding: 0;
        list-style-type: none;
    }

    li {
        margin-top: 5px;
    }

    p {
        display: inline;
        margin: 0px 2px 0px 2px;
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