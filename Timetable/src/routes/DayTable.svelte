<script>
    import Lesson from './Lesson.svelte';

    let {time, day, lessons, editLesson, deleteLesson} = $props(); 
</script>

<div class="grow mx-5 shadow-xl rounded-xl">
    <h1 class="w-100% text-2xl text-white text-center bg-blue-500 rounded-xl">{day.name}</h1>
    <ol class="m-auto w-100%">
        {#each lessons as lesson}
        <Lesson time={time} lessonData={lesson} editLesson={editLesson} deleteLesson={deleteLesson}/>
        {/each}
    </ol>
</div>

