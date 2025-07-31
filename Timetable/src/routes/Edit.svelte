<script>
    let props = $props();

    const checkString = () => {
        return checkDataString() + checkLessonsString();
    }

    const checkDataString = () => {
        let errors = "";
        if (!props.edittedLesson.name.trim() || props.edittedLesson.name.length == 0){
            errors+= "Name is empty, \n";
        }
        if (props.edittedLesson.hour.length == 0 || isNaN(props.edittedLesson.hour) ||  props.edittedLesson.hour > 23 || props.edittedLesson.hour < 0){
            errors+= "Hour is incorrect, \n";
        }
        if (props.edittedLesson.minute.length == 0 || isNaN(props.edittedLesson.minute) || props.edittedLesson.minute > 59 || props.edittedLesson.minute < 0){
            errors+= "Minute is incorrect, \n";
        }
        if (props.edittedLesson.day < 0){
            errors+= "Weekday is incorrect, \n";
        }

        return errors;

    };

    const checkLessonsString = () => {
        if(props.lessons.filter(x => x.hour == props.edittedLesson.hour && x.minute == props.edittedLesson.minute && props.edittedLesson.day == x.day).length > 0){
            return "Lesson has the same time as a different lesson, \n";
        }else{
            return " \n";
        }
        
    }

</script>

<div class="m-auto w-fit">  
    <div class="flex flex-row m-auto mt-2 w-100%">
        <label class="basis-2/5 grow" for="name">Name</label>
        <input 
        class="basis-3/5 grow border-1 border-gray-200 shadow-xl rounded-lg"
        type="text"
        name="name"
        id="name"
        oninput={(e) => props.onInputChange({[e.target.name]: e.target.value})}
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
        oninput={(e) => props.onInputChange({[e.target.name]: e.target.value})}
        value={props.edittedLesson.hour === -1 ? "" : props.edittedLesson.hour}
        />
        </div>
        <div class="flex flex-row m-auto mt-2 w-100%">
        <label class="basis-2/5 grow" for="minute">Minute</label>
        <input type="text" class="basis-3/5 grow border-1 border-gray-200 shadow-xl rounded-lg" name="minute" id="minute"
        oninput={(e) => props.onInputChange({[e.target.name]: e.target.value})}
        value={props.edittedLesson.minute === -1 ? "" : props.edittedLesson.minute}
        />
    </div>
    <div class="flex flex-row m-auto mt-2 w-100%">
    <span class="basis-1 text-red-500 text-center grow">{checkString()}</span>
    </div>
    <div class="flex flex-row h-full m-auto mt-2 w-100%">
    <button class="basis-1/2 grow border-1 border-gray-200 shadow-xl rounded-lg" disabled={checkString().trim().length>0} onclick={()=>props.onSave()}>OK</button>
    <button class="basis-1/2 grow border-1 border-gray-200 shadow-xl rounded-lg" onclick={()=>props.clearEdit()}>Cancel</button>
    </div>
</div>