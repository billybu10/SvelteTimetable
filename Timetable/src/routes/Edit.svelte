<script>
    let props = $props();
</script>

<div class="m-auto w-fit">  
    <div class="flex flex-row m-auto mt-2 w-100%">
        <label class="basis-2/5 grow" for="name">Name</label>
        <input 
        class="basis-3/5 grow border-1 border-gray-200 shadow-xl rounded-lg"
        type="text"
        name="name"
        id="name"
        onchange={(e) => props.onInputChange({[e.target.name]: e.target.value})}
        value={props.edittedLesson.name}
        />
    </div>
    <div class="flex flex-row m-auto mt-2 w-100%">
        <label class="basis-1/2 grow mr-1" for="day">Weekday</label>
        <select 
        class="basis-1/2 grow border-1 border-gray-200 shadow-xl rounded-lg"
        type="text"
        name="day"
        id="day"
        onchange={(e) => props.onInputChange({[e.target.name]: e.target.value})}
        value={props.edittedLesson.day === -1 ? "" : props.edittedLesson.day}
        >
            <option value="1">Monday</option>
            <option value="2">Tuesday</option>
            <option value="3">Wednesday</option>
            <option value="4">Thursday</option>
            <option value="5">Friday</option>
            <option value="6">Saturday</option>
            <option value="0">Sunday</option>
        </select>
    </div>
    <div class="flex flex-row m-auto mt-2 w-100%">
        <label class="basis-2/5 grow" for="hour">Hour</label>
        <input type="text"
        class="basis-3/5 grow border-1 border-gray-200 shadow-xl rounded-lg"
        name="hour"
        id="hour"
        onchange={(e) => props.onInputChange({[e.target.name]: e.target.value})}
        value={props.edittedLesson.hour === -1 ? "" : props.edittedLesson.hour}
        />
        </div>
        <div class="flex flex-row m-auto mt-2 w-100%">
        <label class="basis-2/5 grow" for="minute">Minute</label>
        <input type="text" class="basis-3/5 grow border-1 border-gray-200 shadow-xl rounded-lg" name="minute" id="minute"
        onchange={(e) => props.onInputChange({[e.target.name]: e.target.value})}
        value={props.edittedLesson.minute === -1 ? "" : props.edittedLesson.minute}
        />
    </div>
    <div class="flex flex-row m-auto mt-2 w-100%">
    <button class="basis-1/2 grow border-1 border-gray-200 shadow-xl rounded-lg" onclick={()=>props.onSave()}>OK</button>
    <button class="basis-1/2 grow border-1 border-gray-200 shadow-xl rounded-lg" onclick={()=>props.clearEdit()}>Cancel</button>
    </div>
</div>