<template>
    <div class="film-page">
        <div class="container" v-if="film">
            <h1>{{ film.title }}</h1>
            <img
                    :src="film.img"
                    :alt="film.title"
            >
            <div class="section">
                <p class="section__title">Немного о сюжете:</p>
                <p class="section__description">{{ film.description }}</p>
            </div>
            <div class="section">
                <p class="section__title">Рейтинг:</p>
                <p class="section__description">{{ film.rating }}</p>
            </div>
            <div class="section">
                <p class="section__title">Актерский состав:</p>
                <p class="section__description">{{ film.actors.join(', ') }}</p>
            </div>
            <div class="section">
                <p class="section__title">Режиссёры:</p>
                <p class="section__description">{{ film.directors.join(', ') }}</p>
            </div>
<router-link class="back"
                        :to="{ name: 'films' }"
                >
                   Назад к фильмам
                </router-link>
        </div>
       
    </div>

</template>

<script>
    import films from '../mosks/films';

    export default {
        data() {
            return {
                film: null
            }
        },
        created() {
            //params.id - string, film.id - number => поэтому ==  
            const film = films.find(film => film.id == this.$route.params.id);

            if (film) {
                this.film = film
            }else {
                alert('Запрашиваемого фильма нету')
                this.$router.push({name:'films'})
            }
        }
    }
</script>

<style lang="scss" scoped>
    .film-page {
        padding-bottom: 100px;
        .back {
            color: #ffffff;
    
            margin-top: 30px;
            padding: 2px 4px;
            background-color: #EB5804;
            text-decoration: none;
            border-radius: 5px;
            justify-content: center;
            display: flex;
            width: max-content;
            
        }
        h1 {
            color: #ffffff;
            margin-bottom: 30px;
            padding-bottom: 15px;
            position: relative;
            &::before {
                content: '';
                position: absolute;
                width: 100%;
                height: 3px;
                bottom: 0;
                left: 0;
                background: linear-gradient(90deg, #EB5804 0%, rgba(0,0,0,0) 90%);
            }
        }
        img {
            object-fit: cover;
            border-radius: 10px;
            width: 1160px;
            height: 600px;
            margin-bottom: 30px;
        }
        .section {
            &__title {
                color: #EB5804;
                font-weight: 700;
                font-size: 25px;
                margin-bottom: 10px;
            }
            &__description {
                color: #ffffff;
                font-size: 18px;
                line-height: 30px;
            }
        }
      
    }
</style>
