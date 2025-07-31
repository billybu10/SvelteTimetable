<script>
    import { onMount } from 'svelte';
    import uniqid from 'uniqid';
    import DayTable from "./DayTable.svelte"
    import Edit from './Edit.svelte'

    const weekdays = [
        {name: "Monday", number: "1"},
        {name: "Tuesday", number: "2"},
        {name: "Wednesday", number: "3"},
        {name: "Thursday", number: "4"},
        {name: "Friday", number: "5"},
        {name: "Saturday", number: "6"},
        {name: "Sunday", number: "0"}
    ]

    let time = $state(new Date());

    let lessons = $state([]);
    let edittedLesson = $state({
                id: uniqid(),
                name: "",
                day: -1,
                hour: -1,
                minute: -1,
            });

    onMount(() => {
		lessons = JSON.parse(localStorage.getItem("Lessons")) || [];
        
        setInterval(() => {time = new Date()}, 1000);
	});

    const clearEdit = () => {
        edittedLesson = {
                id: uniqid(),
                name: "",
                day: -1,
                hour: -1,
                minute: -1,
            };
    }

    const deleteLesson = (id) => {
        lessons = lessons.filter((element) => element.id != id);
        localStorage.setItem("Lessons", JSON.stringify(lessons))
    }

    const addLesson = (val) => {
        edittedLesson = Object.assign(edittedLesson, val);
    }

    const saveLesson = () => {
        let lessonExistsIndex = lessons.findIndex(element => element.id === edittedLesson.id);
        if (lessonExistsIndex > -1) {
            lessons[lessonExistsIndex] = edittedLesson;
        }else{
            lessons.push(edittedLesson);
        }
        clearEdit();
        localStorage.setItem("Lessons", JSON.stringify(lessons));
    }

    const editLesson = (id) => {
        edittedLesson = {...lessons.find(element => element.id === id)};
    }

</script>

<div>
    {#each weekdays as weekday}
        {#if lessons.filter(x => x.day === weekday.number).length > 0}
            <DayTable time={time} day={weekday} lessons={lessons.filter(x => x.day === weekday.number)} editLesson={editLesson} deleteLesson={deleteLesson}/>
        {/if}
        
    {/each}
</div>

<Edit edittedLesson = {edittedLesson} lessons={lessons} onInputChange={addLesson} onSave={saveLesson} clearEdit={clearEdit}/>