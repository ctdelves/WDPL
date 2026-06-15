<script>
document.addEventListener('DOMContentLoaded', () => {
  document.querySelectorAll("th").forEach(header => {
    header.style.cursor = "pointer";
    header.addEventListener("click", () => {
      const table = header.closest("table");
      const index = Array.from(header.parentNode.children).indexOf(header);
      const rows = Array.from(table.querySelectorAll("tbody tr"));
      const asc = header.classList.toggle("asc");

      rows.sort((a, b) => {
        const A = a.children[index].innerText.trim();
        const B = b.children[index].innerText.trim();
        return asc
          ? A.localeCompare(B, undefined, { numeric: true })
          : B.localeCompare(A, undefined, { numeric: true });
      });

      rows.forEach(r => table.querySelector("tbody").appendChild(r));
    });
  });
});
</script>
