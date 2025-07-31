<script>
    let {time, lessonData, editLesson, deleteLesson} = $props();
</script>

<div class="w-95/100 m-auto my-5 flex flex-row">
    <span class="grow text-center basis-3/5">{lessonData.hour}:{lessonData.minute} - {lessonData.name}</span> 
    <button class="grow basis-1/5 border-2 border-gray-200 shadow-xl rounded-lg" onclick={()=>editLesson(lessonData.id)}>Edit</button>  
    <button class="grow basis-1/5 border-2 border-gray-200 shadow-xl rounded-lg" onclick={()=>deleteLesson(lessonData.id)}>Delete</button> 
</div>