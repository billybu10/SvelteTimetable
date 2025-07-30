<script>
    import Lesson from './Lesson.svelte';

    let {time, dayName, lessons} = $props(); 
</script>

<h1>{dayName}</h1>
<ol>
    {#each lessons as lesson}
    <Lesson time={time} lessonData={lesson}/>
    {/each}
</ol>