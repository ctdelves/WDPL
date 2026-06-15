---
layout: default
---

# League Table

| Team | Played | Matches Won | Frames For | Frames Against | Points |
|------|--------|-------------|------------|----------------|--------|
| Fox | 4 | 4 | 35 | 9 | 47 |
| RBL | 4 | 2 | 27 | 17 | 33 |
| Two Brewers A | 4 | 2 | 23 | 21 | 29 |
| POW A | 4 | 2 | 23 | 21 | 29 |
| Nags | 4 | 2 | 21 | 23 | 27 |
| Two Brewers B | 4 | 2 | 18 | 26 | 24 |
| POW B | 4 | 2 | 17 | 27 | 23 |
| Swan | 4 | 0 | 12 | 32 | 12 |

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
