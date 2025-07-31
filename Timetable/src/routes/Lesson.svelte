<script>
    let {time, lessonData, editLesson, deleteLesson} = $props();
</script>

<div>
    {lessonData.hour}:{lessonData.minute} - {lessonData.name} 
    <button onclick={()=>editLesson(lessonData.id)}>Edit</button>  
    <button onclick={()=>deleteLesson(lessonData.id)}>Delete</button> 
</div>