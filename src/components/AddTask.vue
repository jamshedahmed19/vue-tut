<template>
    <form @submit="onSubmit">
        <div class="form-control">
            <label>Task</label>
            <input type="text" name="text" v-model="text" placeholder="Add Task" />
        </div>
        <div class="form-control">
            <label>Day & Time</label>
            <input type="text" name="day" v-model="day" placeholder="Add Day & Time" />
        </div>
        <div class="form-control form-control-check">
            <label>Set Reminder</label>
            <input type="checkbox" name="reminder" v-model="reminder" />
        </div>

        <input type="submit" value="Save Task" class="btn btn-block" />
    </form>
</template>

<script>
import { mapActions } from 'vuex';

export default {
    name: "AddTask",
    data() {
        return {
            id: '',
            text: '',
            day: '',
            reminder: false
        }
    },
    methods: {
        ...mapActions(['addTask']),
        onSubmit(e) {
            e.preventDefault();
            if (!this.text) {
                alert("Please enter a task");
            }

            this.addTask({
                text: this.text,
                day: this.day,
                reminder: this.reminder
            })

            this.task = '';
            this.day = '';
            this.reminder = false;
        }
    },
}

</script>


<style scoped>
.add-form {
    margin-bottom: 40px;
}

.form-control {
    margin: 20px 0;
}

.form-control label {
    display: block;
}

.form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}

.form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.form-control-check label {
    flex: 1;
}

.form-control-check input {
    flex: 2;
    height: 20px;
}
</style>