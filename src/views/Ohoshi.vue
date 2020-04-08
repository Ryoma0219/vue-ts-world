<template>
  <div>
    <div>{{ getFullName() }}</div>
    <div>{{ handleId }}: {{ name }}</div>
    <button @click="increment">button</button>
    <div>
      <input type="text" v-model="text" />
    </div>
    {{ doubleText }}
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop, Watch } from "vue-property-decorator";

@Component
export default class Ohoshi extends Vue {
  @Prop() private message!: string;
  id = 0;
  firstName = "Ryoma";
  familyName = "Hoshino";
  name = "Ryoma";
  text = "hoge";

  created(): void {
    console.log("created");
  }

  @Watch("id")
  onChangeId(value: number, oldValue: number): void {
    console.log(`[Watch] value: ${value}, oldValue: ${oldValue}`);
  }

  get handleId(): number {
    return this.id;
  }

  get doubleText(): string {
    let complexText = "";
    for (let i = 0; i < 2; i++) {
      complexText += this.text;
    }
    return complexText;
  }

  getFullName(): string {
    return `${this.firstName} ${this.familyName}`;
  }

  increment(): void {
    this.id += 1;
  }
}
</script>
