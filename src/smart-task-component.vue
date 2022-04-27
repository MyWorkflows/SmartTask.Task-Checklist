<template> 
    <div class="col-md-12">
     <div class="fv-row mb-5">
       <template v-for="task in model.taskChecklist" :key="task.id">
            <div class="d-flex align-items-center mb-2 py-3 bg-white">
												<!--begin::Bullet-->
												<span class="bullet bullet-vertical h-40px"></span>
												<!--end::Bullet-->
												<!--begin::Checkbox-->
												<div class="form-check form-check-custom form-check-solid mx-5">
													<input class="form-check-input" type="checkbox" value="">
												</div>
												<!--end::Checkbox-->
												<!--begin::Description-->
											<div class="flex-grow-1">
													<a href="#" class="text-gray-800 text-hover-primary fw-bolder fs-6">{{task.taskName}}</a>
													<span class="text-muted fw-bold d-block" v-html="task.taskDescription"></span>
											</div>
						 </div>
        </template>
    </div>
  <button class="btn btn-sm btn-success">Mark all as complete</button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SmartTaskComponent",
  props: ['componentState', 'componentStatus'],
  data() {
    return { model: {} };
  },
  computed: {},
  methods: {
    async submitForm() {
      this.$emit("execute-smart-task", this.model);
    }
  },
  created() {
    if (this.componentState) {
      this.model = this.componentState;
    }
  },
  setup() {},
});
</script>
