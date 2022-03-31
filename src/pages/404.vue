<template>
    <div class="not-found">
        <h1>
            Ничего не найдено
        </h1>
        <router-link class="back"
                        :to="{ name: 'main' }"
                >
                   Назад к фильмам
                </router-link>
    </div>
</template>

<style lang="scss" scoped>
    .not-found {
         display: flex;
         flex-direction: column;
         justify-content: center;
         align-items: center;
         min-height: 100vh;
         h1 {
             color: #ffffff;
             font-size: 70px;
             margin-bottom: 20px;
         }
         
     }
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
</style>
