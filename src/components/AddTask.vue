<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input 
                type="text" 
                v-model="text" 
                name="text" 
                placeholder="Add Task" 
            />
        </div>
        <div class="form-control">
            <label>Day & Time</label>
            <input 
                type="text"
                v-model = "day"
                name="day"
                placeholder="Add Day & Time"
            />
        </div>
        <div class="form-control form-control-check">
            <label>
                Set Reminder
            </label>
            <input 
                type="checkbox" 
                v-model="checkbox"
            />
        </div>
    </form>
</template>