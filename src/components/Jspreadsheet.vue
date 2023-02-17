<template>
  <div ref="container" />
  <br />
  <input
    type="button"
    @click="addNewRow"
    value="Add new row"
    class="jss_object"
  />
  <input
    type="button"
    @click="showData"
    value="Add new row"
    class="jss_object"
  />
  {{ instance }}
</template>
<script>
import { ref } from "vue";
import jspreadsheet from "jspreadsheet";
import "jspreadsheet/dist/jspreadsheet.css";
import "jsuites/dist/jsuites.css";

export default {
  name: "Jspreadsheet",
  props: {
    options: {
      type: Object,
      require: true,
    },
  },
  setup(props) {
    const container = ref(null);
    const options = props.options ? { ...props.options } : {};
    const instance = ref(0);

    return { container, options, instance };
  },

  mounted() {
    // Register license
    jspreadsheet.setLicense(
      "OTJhODY0Mzk0MGU5ZTFlOWUyOTAwNmZjZThjOWU4YWMxNTA0ZGM0NjZhZTY5Y2UzMDllYjZmZTFkZjZkYTI2YWZhMmIxYWRmMzk5MWE4YzExNjRlZjdiZDY4Zjc0NmIzZGFlYzNmNDdlZTVkMmI0Mjg3ZjkxN2MwNTYzNDNjNjUsZXlKdVlXMWxJam9pU25Od2NtVmhaSE5vWldWMElpd2laR0YwWlNJNk1UWTVPRGc0TXpJd01Dd2laRzl0WVdsdUlqcGJJbXB6YUdWc2JDNXVaWFFpTENKcWMzQnlaV0ZrYzJobFpYUXVZMjl0SWl3aVkzTmlMbUZ3Y0NJc0luVmxMbU52YlM1aWNpSXNJblZ1YVhSbFpDNWxaSFZqWVhScGIyNGlMQ0ozWldJaUxDSnBiblJ5WVhOb1pXVjBjeTVqYjIwaUxDSmpiMlJsYzJGdVpHSnZlQzVwYnlJc0luTm9aV1YwY3k1elptTnZaR1ZpYjNRdVkyOXRJaXdpYkc5allXeG9iM04wSWwwc0luQnNZVzRpT2lJek1TSXNJbk5qYjNCbElqcGJJblkzSWl3aWRqZ2lMQ0oyT1NJc0ltWnZjbTF6SWl3aVptOXliWFZzWVNJc0luSmxibVJsY2lJc0luQmhjbk5sY2lJc0ltbHRjRzl5ZEdWeUlpd2lkbUZzYVdSaGRHbHZibk1pTENKamIyMXRaVzUwY3lJc0luTmxZWEpqYUNJc0ltTm9ZWEowY3lJc0ltTnNiM1ZrSWl3aVltRnlJaXdpY0hKcGJuUWlMQ0p0WVhOcklpd2ljMmhsWlhSeklpd2ljMlZ5ZG1WeUlpd2lhVzUwY21GemFHVmxkSE1pWFgwPQ=="
    );
    // Create Jspreadsheet
    this.instance = jspreadsheet(this.container, this.options);
  },
  methods: {
    addNewRow() {
      this.instance[0].insertRow();
    },
    showData() {
      console.log(this.instance[0].getStyle());
      this.instance[0].setStyle({ B1: "font-weight: bold" });
    },
  },
};
</script>