<template>
  <Jspreadsheet :options="Options" />
</template>

<script>
import Jspreadsheet from "./components/Jspreadsheet";

export default {
  components: {
    Jspreadsheet,
  },
  setup() {
    const Options = {
      toolbar: true,
      worksheets: [
        {
          data: [[1, 2, 3, 4]],
          minDimensions: [100, 100],
          tableOverflow: true,
          freezeColumns: 2,
        },
      ],
    };
    return { Options };
  },
};
</script>