<template>
  <div>
    <h1>Grade Calculator</h1>
    <div class="container-fluid">
      <div class="row">
        <div class="col-sm-12 col-lg-12">
          <table class="table">
            <thead>
              <tr>
                <th scope="col">Subject Code</th>
                <th scope="col">Subject</th>
                <th scope="col">Credit</th>
                <th scope="col">Grade</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="dataSubject in dataSubjects" :key="dataSubject.id">
                
                <td>{{dataSubject.subjectCode}}</td>
                <td>{{dataSubject.subject}}</td>
                <td>{{dataSubject.credit}}</td>
                <td>
                  <select class="form-control-sm" v-model.number="dataSubject.value">
                    <option value=0>W</option>
                    <option value=4>A</option>
                    <option value=3.5>B+</option>
                    <option value=3>B</option>
                    <option value=2.5>C+</option>
                    <option value=2>C</option>
                    <option value=1.5>D+</option>
                    <option value=1>D</option>
                    <option value=0>E</option>
                  </select>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="col-sm-12 col-lg-12">
          <div class="Cal">
            <div :class="statusClass">{{status}}</div>
            <div class="credit">หน่วยกิตรวม {{creditAll}}{{creditLost}}</div>
            <div class="btCal" @click="calculator">Calculator</div>
          </div>
          
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data: function() {
    return {
      statusClass:"status",
      creditAll:0,
      creditLost:'',
      status:"ป้อนเกรดของคุณ",
      dataSubjects: [
        { subjectCode: '240-101', subject: 'Introduction to Computer Programming', credit: 3, value:0 },
        { subjectCode: '240-201', subject: 'Computer Engineering Software Laboratory I', credit: 1, value:0 },
        { subjectCode: '240-202', subject: 'Computer Engineering Hardware Laboratory I', credit: 1, value:0 },
        { subjectCode: '240-203', subject: 'Computer Engineering Software Laboratory II', credit: 1, value:0 },
        { subjectCode: '240-204', subject: 'Computer Engineering Hardware Laboratory II', credit: 1, value:0 },
        { subjectCode: '240-205', subject: 'Electric Circuits', credit: 3, value:0 },
        { subjectCode: '240-206', subject: 'Introduction to Computer Networks', credit: 3, value:0 },
        { subjectCode: '240-207', subject: 'Programming and Data Structures', credit: 3, value:0 },
        { subjectCode: '240-208', subject: 'Digital Logic and Design', credit: 3, value:0 },
        { subjectCode: '240-209', subject: 'Basic Electronics', credit: 3, value:0 },
        { subjectCode: '240-210', subject: 'Programming Techniques', credit: 2, value:0 },
        { subjectCode: '240-211', subject: 'Software Engineering', credit: 2, value:0 },
        { subjectCode: '240-212', subject: 'Probability and Statistics', credit: 3, value:0 },
        { subjectCode: '240-213', subject: 'Discrete Mathematics', credit: 2, value:0 },
        { subjectCode: '240-214', subject: 'Data Communications and Networking', credit: 3, value:0 },
        { subjectCode: '240-215', subject: 'Computer Engineering Mathematics', credit: 3, value:0 },
        { subjectCode: '240-301', subject: 'Advanced Computer Engineering Laboratory I', credit: 1, value:0 },
        { subjectCode: '240-303', subject: 'Ethical, Legal and Social Issues in Computer Profession', credit: 1, value:0 },
        { subjectCode: '240-304', subject: 'Computer Operating Systems', credit: 3, value:0 },
        { subjectCode: '240-305', subject: 'Database Systems', credit: 3, value:0 },
        { subjectCode: '240-306', subject: 'Wireless and Mobile Computing', credit: 2, value:0 },
        { subjectCode: '240-307', subject: 'Computer Architecture and Organization', credit: 3, value:0 },
        { subjectCode: '240-321', subject: 'Design Architecture and Engineering for Intelligent Systems', credit: 3, value:0 },

      ]
    }
  },
  methods: {
    calculator: function() {
       this.creditAll=0
       console.log("",(53*80/100))
       console.log(this.dataSubjects[0].value);
       for(var i=0;i<23; i++){
          if(this.dataSubjects[i].value>0){
            this.creditAll=this.creditAll+this.dataSubjects[i].credit
            console.log("Credit:",this.creditAll)
            if(this.creditAll>=(53*80/100)){
              this.creditLost = ' ผ่านเกณฑ์'          
              this.status='Pass'
              this.statusClass='Pass'
            }
            else if(this.creditAll<(53*80/100)){
              let x = 53-(this.creditAll)
              this.creditLost = ' ขาดอีก '+ x
              this.status='False'
              this.statusClass='NoPass'
            }
          }
       }
    }
  },
  
};
</script>
<style scoped>
.table {
  font-family: 'Varela Round', sans-serif;
}
.container-fluid{

}
.subject {
  background-color: aquamarine;
}
.Cal {
  align-items: center;
  justify-content: center;
  display: flex;
  padding: 10px;
}
.btCal {
  user-select: none;
  cursor: pointer;
  align-items: center;
  justify-content: center;
  display: flex;
  width: 200px;
  height: 50px;
  background-color: #174873;
  color: #fff;
  font-size: 25px;
}
.btCal:hover{
  background-color: #1a609c;
}
.credit{
  font-family: 'Prompt', sans-serif;
  font-size: 20px;
  padding: 20px;
}
.status {
  align-items: center;
  justify-content: center;
  display: flex;
  width: 200px;
  height: 50px;
  background-color: #174873;
  padding: 20px;
  font-size: 20px;
  color: #fff;
  font-family: 'Prompt', sans-serif;
}
.NoPass {
  align-items: center;
  justify-content: center;
  display: flex;
  width: 200px;
  height: 50px;
  background-color: #ff0000;
  padding: 20px;
  font-size: 20px;
  color: #fff;
  font-family: 'Prompt', sans-serif;
}
.Pass {
  align-items: center;
  justify-content: center;
  display: flex;
  width: 200px;
  height: 50px;
    background-color: #1c8d2f;
  padding: 20px;
  font-size: 20px;
  color: #fff;
  font-family: 'Prompt', sans-serif;
}
</style>
