<template>
    <div>
        <h1>{{item.name}}の天気情報</h1>
        <ul>
            <li>天気:{{item.weather[0].main}}</li>
            <li>温度:{{item.main.temp}}℃</li>
            <li>湿度:{{item.main.humidity}}%</li>
            <li>風速:{{item.wind.speed}}m</li>
        </ul>

        <nuxt-link to="/">トップに戻る</nuxt-link>
    </div>
</template>

<script>
    export default {
        async asyncData({route, app}) {
            const item = await app.$axios.$get(`https://api.openweathermap.org/data/2.5/weather?q=${route.params.name},jp&units=metric&appid=77c60a764b6381bd27797af9e10a1386`)
            return {
                item
            }
        }
    }
</script>
