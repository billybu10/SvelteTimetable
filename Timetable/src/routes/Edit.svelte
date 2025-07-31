<script>
    let props = $props();
</script>

<div class="Edit">  
    <div class="Edit_inputgroup">
        <label for="name">Name</label>
        <input 
        type="text"
        name="name"
        id="name"
        onchange={(e) => props.onInputChange({[e.target.name]: e.target.value})}
        value={props.edittedLesson.name}
        />
    </div>
    <div class="Edit_inputgroup">
        <label for="dzien">Choose weekday</label>
        <select 
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
    <div class="Edit_inputgroup">
        <label for="czasG">Hour</label>
        <input type="text"
        name="hour"
        id="hour"
        onchange={(e) => props.onInputChange({[e.target.name]: e.target.value})}
        value={props.edittedLesson.hour === -1 ? "" : props.edittedLesson.hour}
        />
        </div>
        <div class="Edit_inputgroup">
        <label for="czasM">Minute</label>
        <input type="text" name="minute" id="minute"
        onchange={(e) => props.onInputChange({[e.target.name]: e.target.value})}
        value={props.edittedLesson.minute === -1 ? "" : props.edittedLesson.minute}
        />
    </div>
    <div class="Edit_inputgroup">
    <button onclick={()=>props.onSave()}>OK</button>
    <button onclick={()=>props.clearEdit()}>Cancel</button>
    </div>
</div>