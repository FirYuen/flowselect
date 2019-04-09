<template>
  <div class="hello">
    <el-cascader :options="options" v-model="result" :show-all-levels="false" popper-class="aaaa"></el-cascader>
    <el-button @click="showResult">show Result</el-button>
    <el-dialog :title="currentResult.title" :visible.sync="dialogVisible" width="80%">
      <span>{{currentResult.text}}</span>
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
        result1: {
          title: "FOLLOW-UP TASK",
          text:
            "Complete handover steps and send a follow-up task to the appropriate queue."
        },

        result2: {
          title: "COLD HANDOVER",
          text:
            "Complete handover steps and send a follow-up task to the appropriate queue."
        },
        result3: {
          title: "COLD HANDOVER",
          text:
            "Keep the case and continue working with your customer on your next shift"
        },

        result4: {
          title: "WARM HANDOVER",
          text:
            "Complete handover steps and send a follow-up task to the appropriate queue."
        }
      },
      options: [
        {
          value: "node0",
          label: "Why is handover needed",
          children: [
            {
              value: "node1",
              label: "Contact needed outside of case owner hours",
              children: [
                {
                  value: "result1",
                  label:
                    "Quick follow up action outside of case owner working hours",
                  children: [
                    {
                      value: "result1",
                      label: "FOLLOW-UP TASK"
                    }
                  ]
                },
                {
                  value: "result2",
                  label:
                    "Cx has requested to work outside the work hours of the owning Engineer",
                  children: [
                    {
                      value: "result2",
                      label: "COLD HANDOVER"
                    }
                  ]
                }
              ]
            },
            {
              value: "node2",
              label: "Case owner is approaching end day",
              children: [
                {
                  value: "node3",
                  label: "Is customer avaliavle to continue?",
                  children: [
                    {
                      value: "no",
                      label: "No",
                      children: [
                        {
                          value: "node4",
                          label: "Cx would like to continue at annother time",
                          children: [
                            {
                              value: "result2",
                              label:
                                "Callback will be outside of case owner work hours",
                              children: [
                                {
                                  value: "result2",
                                  label: "COLD HANDOVER"
                                }
                              ]
                            },
                            {
                              value: "result3",
                              label:
                                "Callback is agreed during case owner avaliability",
                              children: [
                                {
                                  value: "result3",
                                  label: "DO NOT HANDOVER"
                                }
                              ]
                            }
                          ]
                        }
                      ]
                    },
                    {
                      value: "yes",
                      label: "Yes",
                      children: [
                        {
                          value: "result4",
                          label: "Cx requests continue until resolution",
                          children: [
                            {
                              value: "result4",
                              label: "WARM HADNOVER"
                            }
                          ]
                        }
                      ]
                    }
                  ]
                }
              ]
            }
          ]
        }
      ]
    };
  },
  methods: {
    showResult: function() {
      let lastResult = this.result[this.result.length - 1];
      this.currentResult = this.results[lastResult];
      this.dialogVisible = true;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.el-cascader {
  width: 600px;
}
.aaaa {
  height: 400px;
  border: 1px solid red;
}
</style>
