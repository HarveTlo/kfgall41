<template>
  <div class="table p-10 w-full">
    <table class="my-table w-full border border-b rounded-lg">
      <colgroup>
        <col span="1" style="width: 15%;" />
        <col span="1" style="width: 15%;" />
        <col span="1" style="width: 15%;" />
        <col span="1" style="width: 15%;" />
        <col span="1" style="width: 40%;" />
      </colgroup>
      <thead>
        <th>Teacher Name</th>
        <th>Gender</th>
        <th>Phone Number</th>
        <th>Date of Birth</th>
        <th>ID Card number</th>
      </thead>

      <tbody id="table-body">
        <tr
          v-for="i in Object.keys(tableData).length"
          :id="`row${i}`"
          :key="`row${i}`"
          class="table-row border-b border-black"
        >
          <td v-for="field in fields" :key="`row${i}-col${field}`" class="">
            <input
              :class="`input-row-${i} w-full`"
              v-model="tableData[`row${i}`][field]"
              :type="field==='phone'?'tel': field==='date'?'date':'text'"
              placeholder="value"
              @focus="inputFocused(i)"
            />
          </td>
        </tr>
      </tbody>
    </table>

    <div class="flex justify-evenly action-buts">
      <button @click="addEntry">Add Teacher</button>
      <button @click="deleteEntry">Remove Teacher</button>
      <button @click="save">Save Teacher</button>
      
    </div>

    <div v-show="showPopup" class="add-form-div">
        <div class="add-form">
            <div class="name-input">
                <div>Teacher Name:</div>
                <input v-model="formData.name" type="text" placeholder="enter name">
            </div>
            <div class="gender-input">
                <div>Gender:</div>
                <input v-model="formData.gender" type="text" placeholder="enter gender (F or M)">
            </div>
            <div class="phone-input">
                <div>Phone Number:</div>
                <input v-model="formData.phone" type="tel" placeholder="enter phone number">
            </div>
            <div class="date-input">
                <div>Date of Birth:</div>
                <input v-model="formData.date" type="date" placeholder="enter date">
            </div>
            <div class="card-input">
                <div>ID Card Number:</div>
                <input v-model="formData.cardNumber" type="text" placeholder="enter card number">
            </div>

            <div class="add-buts">
                <button @click="cancelPopup">Cancel</button><button @click="saveTeacher">Save</button>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Tables",

  data() {
    return {
      num_rows: 10,
      isEditMode: true,
      selectedRow: null,
      tableData: {},
      fields:['name','gender','phone','date','cardNumber'],
      showPopup:false,

      formData:{
          name:'',
          gender:'',
          phone:'',
          date:'',
          cardNumber:''
      }
    };
  },

  methods: {
    inputFocused(row) {
      const rowElement = document.getElementById(`row${row}`);
      const currentRow = document.getElementById(`row${this.selectedRow}`);

      if (currentRow) currentRow.classList.remove("active");
      rowElement.classList.add("active");
      this.selectedRow = row;

      //   console.log("row ", row, " selected");
    },
    addEntry() {
        this.showPopup=true;
    },


    deleteEntry() {
      const rowElement = document.getElementById(`row${this.selectedRow}`);
      const tableBody = document.getElementById("table-body");

      if (rowElement) {
        tableBody.removeChild(rowElement);
        delete this.tableData[`row${this.selectedRow}`];
        this.selectedRow = null;
      }
    },

    cancelPopup(){
        this.showPopup=false;
    },

    saveTeacher(){
        this.tableData = {...this.tableData, [`row${Object.keys(this.tableData).length+1}`]:this.formData}
        this.showPopup=false;
        console.log(this.tableData);
    },


    save() {
      if (this.isEditMode) {
        this.isEditMode = false;
      }
    }
  },

  created() {
    for (let i = 1; i <= this.num_rows; i++) {
      this.tableData[`row${i}`] = {
        name: "",
        gender: "",
        phone: "",
        date: "",
        cardNumber: ""
      };
    }

    console.log(this.tableData);
  }
};
</script>

<style lang="scss" scoped>
.my-table {
  border: 2px solid green;
  tr td:not(:last-child) {
    border-right: 1px solid green;
  }

  input {
    padding: 5px;
  }
}

.table-row.active input {
  background-color: rgba(191, 240, 191, 0.664);
}
.table-row input:focus {
  outline-color: green;
}
.action-buts {
  margin-top: 30px;
  button {
    background: #ccc;
    padding: 10px 30px;
    border-radius: 5px;
  }

}

.add-form-div{
    position:fixed;
    width:100vw;
    height: 100vh;
    background:rgba(0,0,0,.7);
    top:0;
    left:0;
    z-index: 50;
    display: flex;
    justify-content: center;
    align-items: center;

    .add-form{
        background:white;
        border-radius: 5px;
        min-width: 500px;
        padding:20px;

        input{
            border:1px solid green;
            width:100%;
            border-radius: 5px;
            padding:5px;
                margin-bottom: 15px;

        }

        .add-buts{
            display: flex;
            button{
                background:green;
                color:white;
                padding:10px 30px;
            }
            button:first-child{
                margin-right: 20px;
                background:red;
            }
        }
        
    }
}
</style>
