<template>
  <t-transfer
    :data="items"
    :search="true"
    v-model="targetValue"
    :checked.sync="checked"
    @change="onChange"
    @checked-change="handleCheckedChange"
  >
    <template v-slot:tree="slotProps">
      <t-tree
        :data="slotProps.data"
        v-model="slotProps.value"
        @change="slotProps.onChange"
        checkable
        hover
        expand-all
        transition
      />
    </template>
  </t-transfer>
</template>
<script setup>
import { ref } from 'vue';

const items = ref([
  {
    value: '1',
    label: '1',
    children: [
      {
        value: '1.1',
        label: '1.1',
      },
      {
        value: '1.2',
        label: '1.2',
        children: [
          {
            value: '1.2.1',
            label: '1.2.1',
            children: [
              {
                value: '1.2.1.1',
                label: '1.2.1.1',
              },
              {
                value: '1.2.1.2',
                label: '1.2.1.2',
              },
            ],
          },
        ],
      },
    ],
  },
  {
    value: '2',
    label: '2',
    children: [
      {
        value: '2.1',
        label: '2.1',
      },
      {
        value: '2.2',
        label: '2.2',
      },
    ],
  },
]);
const targetValue = ref([]);
const checked = ref([]);
const handleCheckedChange = ({
  checked, sourceChecked, targetChecked, type,
}) => {
  console.log('handleCheckedChange', {
    checked,
    sourceChecked,
    targetChecked,
    type,
  });
};
const onChange = (newTargetValue) => {
  console.log('onChange', newTargetValue);
};
</script>
