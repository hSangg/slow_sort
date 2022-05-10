<script context="module">
  let lan = 0;
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

  export const bogoSort = (a, n) => {
    while (!isSorted(a, n)) suffle(a);
  };
</script>
