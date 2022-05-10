<script>
  let lan = 0;
  let form;
  let first = false;
  const isSorted = (a, n) => {
    while (--n >= 1) if (a[n] < a[n - 1]) return false;

    return true;
  };

  const suffle = (a) => {
    for (let i = 0; i < a.length; i++) {
      const randomIndex = Math.floor(Math.random() * a.length);
      let temp = a[i];
      a[i] = a[randomIndex];
      a[randomIndex] = temp;
    }
    console.log("day la lan xao tron thu: ", ++lan);
  };

  const handleClick = () => {
    form.reset();
  };

  export const bogoSort = (a, n) => {
    while (!isSorted(a, n)) suffle(a);
  };

  /////////////////////////////////////////////////////////////////

  let button = "sort";
  const handelSubmit = (e) => {
    e.preventDefault();
    const data = e.target[0].value.split(",").map((x) => +x);
    if (!data[0]) {
      button = "vui long nhap mang can sort";
      return;
    }

    bogoSort(data, data.length);
    button = `sau ${lan} xao tron thi cung da xong | ${data[0] ? data : ""}`;
    lan = 0;
    first = true;
  };
</script>

<div class="p-2 flex items-center w-full">
  <form bind:this={form} on:submit={handelSubmit} action="" class="w-full p-2">
    <input
      type="text"
      class="w-full  p-2 "
      placeholder="Nhap vao phan tu mang"
    />
    <button
      on:submit={handelSubmit}
      type="submit"
      class="w-full bg-green-500 p-2">{button}</button
    >
    {#if first}
      <button
        on:click={handleClick}
        type="submit"
        class="w-full bg-green-700 p-2">Thu Lai</button
      >
    {/if}
  </form>
</div>

<style>
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>
