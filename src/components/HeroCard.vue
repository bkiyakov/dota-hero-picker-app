<template>
    <div class="hero-card">
        <h2>{{hero.localized_name}}</h2>
        <img width="256" height="144" :src="'https://api.opendota.com' + hero.img" alt="Hero image"/>
        <table>
        <tbody>
            <tr>
                <p v-bind:key="hero.roles.indexOf(role)" v-for="role in hero.roles">{{role}}</p>
            </tr>
            <tr>
                <td>Primary attribute:</td><td>{{attr}}</td>
            </tr>
            <tr>
                <td>Attack type:</td><td>{{hero.attack_type}}</td>
            </tr>
            <tr>
                <td>Attack:</td><td>{{attack_min}} - {{attack_max}}</td>
            </tr>
            <tr>
                <td>Health:</td><td>{{health}}</td>
            </tr>
            <tr>
                <td>Health regen:</td><td>{{health_regen}}</td>
            </tr>
            <tr>
                <td>Mana:</td><td>{{mana}}</td>
            </tr>
            <tr>
                <td>Mana regen:</td><td>{{mana_regen}}</td>
            </tr>
            <tr>
                <td>Armor:</td><td>{{armor}}</td>
            </tr>
            <tr>
                <td>Movespeed:</td><td>{{move_speed}}</td>
            </tr>
        </tbody>
        </table>
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
        },
        base_attack: function(){
            switch (this.hero.primary_attr) {
                case "agi":
                    return this.hero.base_agi;
                case "str":
                    return this.hero.base_str;
                case "int":
                    return this.hero.base_int;
                default:
                    return 0;
            }
        },
        attack_min: function(){
            return this.hero.base_attack_min + this.base_attack;
        },
        attack_max: function(){
            return this.hero.base_attack_max + this.base_attack;
        },
        health: function(){
            return this.hero.base_health + this.hero.base_str * 20;
        },
        health_regen: function(){
            return Math.floor((this.hero.base_health_regen + this.hero.base_str * 0.1) * 10)/10;
        },
        mana: function(){
            return this.hero.base_mana + this.hero.base_int * 12;
        },
        mana_regen: function(){
            return Math.floor((this.hero.base_mana_regen + this.hero.base_int * 0.05) * 10)/10;
        },
        armor: function(){
            return Math.floor((this.hero.base_armor + this.hero.base_agi * 0.16) * 100)/100;
        },
        move_speed: function(){
            return Math.floor(this.hero.move_speed + this.hero.move_speed * this.hero.base_agi * 0.0005);
        }
    }
}
</script>

<style scoped>
    .hero-card {
        width: 330px;
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

    table {
        margin: auto;
        padding: 0;
    }

    tr {
        margin-top: 5px;
        text-align: center;
    }

    td {
        text-align: left;
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