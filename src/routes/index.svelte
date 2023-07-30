<script context="module">
    export async function load({fetch}){
        const res = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=65ec093c45d5efeacc9c155cd449dcf3&language=en-US&page=1`
        );
        const data = await res.json();
        console.log(data);
        if(res.ok){
            return{
                props:{popular: data.results }
            }
        }
    }

</script>
<!-- 65ec093c45d5efeacc9c155cd449dcf3 -->

<script>
    import PopularMovies from '../components/PopularMovies.svelte';
    import SearchMovies from '../components/SearchMovies.svelte';
    export let popular;
    import {fly} from 'svelte/transition';
</script>

<section in:fly={{y:50,duration:500 , delay:500}} out:fly={{duration:500}}>
    <SearchMovies/>
    <PopularMovies {popular}/>
</section>




