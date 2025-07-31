<script>
    import Lesson from './Lesson.svelte';

    let {time, day, lessons, editLesson, deleteLesson} = $props(); 
</script>

<h1>{day.name}</h1>
<ol>
    {#each lessons as lesson}
    <Lesson time={time} lessonData={lesson} editLesson={editLesson} deleteLesson={deleteLesson}/>
    {/each}
</ol>