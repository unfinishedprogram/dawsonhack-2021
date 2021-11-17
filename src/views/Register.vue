<template>
  <div class="register">
    <div class="panel" id="main">
      <h2>Register</h2>
      <div class="team">
        <form id="teammenu">
          <span>
            <label>Team Name</label>
            <input type="text" v-model="teamData.name" />
          </span>
          <span class="teamMember panel" v-for="(member, i) in teamData.members" :key="member">
            <IconX class="remove icon"  @click="teamData.members.splice(i, 1)" />
            <span class="inputspan">
              <label>Screen Name</label>
              <input id="screenName" type="text" v-model="teamData.members[i].name" />
            </span>
            <span class="inputspan">
              <label>Dawson Student ID</label>
              <input id="studentNumber" type="text" v-model="teamData.members[i].studID" />
            </span>
          </span>
          <button class="addUserButton" @click="teamData.members.push({})">
            add team member +
          </button>
          <button v-if="inputValid" @click="register()">
            register
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<script lang='ts'>
import { defineComponent } from 'vue';

import IconX from '@/components/icons/IconX.vue';

export default defineComponent({
  setup() {
    console.log('setup');
  },
  components: {
    IconX,
  },
  data() {
    return {
      teamData: {
        members: [],
      },
    };
  },

  methods: {
    register() {
      console.log(this.$data.teamData);
    },
  },
});
</script>

<style scoped lang="scss">
.teammenu {
  span {
    display: flex;
    justify-content: space-around;
  }
}

#main {
  min-width: 600px;
  background-color: #e0e0e0;
}

.inputspan {
  label{
    text-align: right;
    vertical-align: middle;
    line-height: 32px;
  }
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.teamMember {
  display: flex;
  flex-direction: column;
  text-align: left;
  .header {
    display: flex;
    justify-content: space-around;
  }
  .remove {
    position:absolute;
    cursor: pointer;
    border-radius: 0.2rem;
    width: 1rem;
    height: 1rem;
    color:red;
    border: 2px solid red;
  }
}
form {
  display: flex;
  flex-direction: column;
  width: fit-content;
  margin-left: auto;
  margin-right: auto;
  * {
    margin: 0.25rem;
  }
  input {
    padding: 0.5rem;
    box-shadow: inset
      0px 0px 5px rgba(1, 1, 1, 0.1),
      2px 2px 5px rgba(1, 1, 1, 0.25);
    border: none;
  }
  label {
    text-align: right;
    font-weight: bold;
    text-align: left;
  }
}

.panel {
  padding: 1rem;
  margin-left: auto;
  margin-right: auto;
  background-color: #f0f0f0;
  width: fit-content;
  box-shadow: 10px 10px 20px rgba(1, 1, 1, 0.2);
  display: flex;
  flex-direction: column;
}

button {
  font-weight: bold;
  font-size: 1rem;
  width: fit-content;
  border: none;
  padding: 0.75rem;
  margin: 1rem;
  background: #89f;
  box-shadow: 5px 5px 10px rgba(1, 1, 1, 0.2);
  cursor: pointer;
  border: 1px solid #abf;
  border-radius: 2px;
  min-width: 100px;
  &:hover {
    background: #78f;
  }
}
</style>
