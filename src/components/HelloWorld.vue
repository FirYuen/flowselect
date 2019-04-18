<template>
  <div class="hello">
    <h2>Why is handover needed?</h2>
    <el-cascader :options="options" v-model="result" :show-all-levels="false" visible-change="test" :change-on-select="false" popper-class="aaaa"></el-cascader>
    <el-button @click="showResult">show Result</el-button>
    <!-- <el-dialog :title="currentResult.title" :visible.sync="dialogVisible" width="80%"> -->
         <el-dialog  :visible.sync="dialogVisible" width="80%">
      <span v-html="currentResult.text"></span>
      <span slot="footer" class="dialog-footer">
        <el-button type="primary" @click="dialogVisible = false">Gotcha</el-button>
      </span>
    </el-dialog>
  </div>
</template>


<script>
export default {
  data() {
    return {
      result: [],
      dialogVisible: false,
      currentResult: {},
      results: {
        result0: {
          // title: "FOLLOW-UP TASK",
          text:
            `<h1>FOLLOW-UP TASK</h1>`
        },

        result1: {
          // title: "COLD HANDOVER",
          text:
            "<h1>COLD HANDOVER</h1>"
        },
        result2: {
          // title: "COLD HANDOVER",
          text:
            `<h1>Do Not Handover</h1>`
        },

        result3: {
          // title: "WARM HANDOVER",
          text:
            `<h1>Warm Handover</h1>`
        },
        result4: {
          title: "",
          text: `
          A consolidated action plan/Information to the customer through email based on data available and details in case to help move the case forward.<br>
          Let the customer know that you are at end of your shift and you will move the case to the queue and that you are removing the 24x7 flag on their case.<br>
          Uncheck 24*7<br>
          Do not set a callback commitment unless you have agreed with the customer on a callback window.
          `
        },
        result5: {
          title: "",
          text: `
          1. Follow the principals of FQR<br>
          2. You take ownership of the case and call+email the customer<br>
          3. Retain the case and update the customer that you will contact them the next time you are in the office<br>
          4. Do not put this case/task back into the queue!<br>
          5. Ensure your OOF message is ON and has the backup details
 `
        },
        result6: {
          title: "",
          text: `
           1. Please validate customer’s work hours and take over the case if continuing troubleshooting
           `
        },
        result7: {
          title: "",
          text: `
         1. Review the need for a callback on weekend – Never push back but do evaluate and discuss the need<br>
2. Please set customer expectations that a callback cannot be guaranteed at a specific time but must be a window<br>
3. Please set the callback for a one-hour window and appropriately set customer expectations that we will do our best to call as close to the beginning of the window as possible<br>
4. Case must be set for 24x7 and customer should be eligible for after hours support else MSaaS won’t assign the case out<br>
`
        },
        result8: {
          title: "",
          text: `
          1. Always assess and update the customer on WHEN will you make the next contact, your work hours/days<br>
          2. We recommend having a buddy program where engineers from these 2 shifts can use each other as backups for the days they are not in the office<br>
`
        },

        result9: {
          title: "",
          text: `
1. Follow-up and close any cases which are ready for closure<br>
2. Identify owners for your case- Work with your peers through all team collaboration channels<br>
3. Update your manager with the list of cases and respective owners<br>
4. Update customers and TAMs on your OOF and share your TM and the new case owner information on every Case and Collaboration Task<br>
<span style="color: red">5. Every case should be updated and have a Summary along with next set of actions</span><br>
6. Turn on your OOF message and ensure your OOF message has your backup information`
        },
        result10: {
          title: "",
          text: `
Manager is accountable for the cases`
        },
        result12: {
          title: "Do Not Handover",
          text: "<h1>Do Not Handover</h1>"
        }
      },
      options: [
        {
          value: "node0",
          label: "No Overlapping work hours",
          children: [
            {
              value: "node10",
              label: "Contact needed outside of case owner hours",
              children: [
                {
                  value: "result0",
                  label:
                    " Quick follow up action outside of case owner work hours"
                  // children: [{ value: "result0", label: "Follow-up Task" }]
                },
                {
                  value: "result1",
                  label:
                    "  Customer has requested to work outside the work hours of the owning engineer"
                  // children: [{ value: "result1", label: "Cold Handover" }]
                }
              ]
            },
            {
              value: "node13",
              label: "Case Owner is approaching end of day",
              children: [
                {
                  value: "node14",
                  label: "Is customer available to continue?",
                  children: [
                    {
                      value: "node15",
                      label: "Customer would like to continue at another time",
                      children: [
                        {
                          value: "result1",
                          label:
                            "Callback will be outside of Case Owner work hours"
                          // children: [
                          //   {
                          //     value: "result1",
                          //     label: "Cold Handover"
                          //   }
                          // ]
                        },
                        {
                          value: "result2",
                          label:
                            "Callback is agreed during case owner availability"
                          // children: [
                          //   {
                          //     value: "result2",
                          //     label: "Do Not Handover"
                          //   }
                          // ]
                        }
                      ]
                    },
                    {
                      value: "result3",
                      label: "Customer requests to continue until resolution"
                      // children: [
                      //   {
                      //     value: "result3",
                      //     label: "Warm Handover"
                      //   }
                      // ]
                    }
                  ]
                }
              ]
            },
            {
              value: "node19",
              label: "Customer just has a query response",
              children: [
                {
                  value: "result4",
                  label: "Do Not Handover"
                }
              ]
            },
            {
              value: "node20",
              label: "Problem Resolved",
              children: [
                {
                  value: "result4",
                  label: "Close the Case"
                }
              ]
            },
            {
              value: "node21",
              label: "Problem Resolved & Customer demand check-in call",
              children: [
                {
                  value: "result4",
                  label: "Follow-up Task"
                }
              ]
            },
            {
              value: "node22",
              label: "Customer is unavailable",
              children: [
                {
                  value: "node23",
                  label: "Email Not res ponding",
                  children: [
                    {
                      value: "result4",
                      label: "Follow the principal of FQR"
                    }
                  ]
                },
                {
                  value: "node24",
                  label: "Issue can be researched independently",
                  children: [
                    {
                      value: "result4",
                      label: "Continue to work the case"
                    }
                  ]
                },
                {
                  value: "node25",
                  label: "Not enough information on the case to troubleshoot",
                  children: [
                    {
                      value: "result4",
                      label: "Reach out to a TA and double check with them"
                    }
                  ]
                }
              ]
            }
          ]
        },
        {
          value: "node1",
          label: "Have Overlapping work hours",
          children: [
            {
              value: "node26",
              label: "Receive a 24*7 case & customer is unavailable",
              children: [
                {
                  value: "result5",
                  label: "Able to reach the customer"
                  // children: []
                },
                {
                  value: "node29",
                  label: "Unable to reach the customer",
                  children: [
                    {
                      value: "result5",
                      label: "Shift is ending"
                    }
                  ]
                }
              ]
            },
            {
              value: "node27",
              label:
                "Former case owner is out of shift & his work hours have no overlap with customer",
              children: [
                {
                  value: "result6",
                  label: "No follow-up task"
                  // children: []
                },
                {
                  value: "node30",
                  label: "A follow-up Task",
                  children: [
                    {
                      value: "result6",
                      label: "Mark as Complete"
                    }
                  ]
                }
              ]
            }
          ]
        },
        {
          value: "node2",
          label: "Weekend Callback",
          children: [
            {
              value: "result7",
              label: "No special situations downtime"
              // children: []
            },
            {
              value: "node31",
              label: "There are situations like planned downtime",
              children: [
                {
                  value: "result7",
                  label:
                    "Multiple parties do work with your managers to proactively line up a resource"
                }
              ]
            }
          ]
        },
        {
          value: "node3",
          label: "Unusual Shifts",
          children: [
            {
              value: "result8",
              label: "Work could be done"
              // children: []
            },
            {
              value: "node32",
              label: "Customer request to work and can’t wait",
              children: [
                {
                  value: "result8",
                  label: "Follow the handover process"
                }
              ]
            }
          ]
        },
        {
          value: "node4",
          label: "OOF",
          children: [
            {
              value: "result9",
              label: "OOF & have case to handover"
            },
            {
              value: "result10",
              label: "Unplanned OOF"
            }
          ]
        },
        {
          value: "result12",
          label: "Speak different language"
          // children: [{ value: "result12", label: "Do Not Handover" }]
        },
        {
          value: "result12",
          label: "In a different time zone than you"
          // children: [{ value: "result12", label: "Do Not Handover" }]
        },
        {
          value: "node7",
          label: "You will be on vacation or training",
          children: [
            {
              value: "result12",
              label:
                "Re-distribute your cases among your team members, prior to your planned OOF"
              // children: [{ value: "result12", label: "Do Not Handover" }]
            }
          ]
        },
        {
          value: "result12",
          label: "Customer is unresponsive"
          // children: [{ value: "result12", label: "Do Not Handover" }]
        }
      ]
    };
  },
  methods: {
    showResult: function() {
      let lastResult = this.result[this.result.length - 1];
      this.currentResult = this.results[lastResult];
      this.dialogVisible = true;
    },
    test:function () {
      console.log('1')
      
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.el-cascader {
  width: 600px;
}
/* .aaaa {
  height: 400px;
  border: 1px solid red;
} */
</style>
