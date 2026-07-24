const cfg = window.EED_CONFIG;
const menuGrid = document.getElementById("menu-grid");

cfg.menu.forEach(item => {
  const card = document.createElement("article");
  card.className = "menu-card";
  card.innerHTML = `
    <div class="menu-icon" aria-hidden="true">${item.icon}</div>
    <h3>${item.name}</h3>
    <p>${item.description}</p>
    <div class="price-row"><span class="price">${item.price} บาท</span><a href="#contact">สั่ง/สอบถาม →</a></div>`;
  menuGrid.appendChild(card);
});

const toggle = document.querySelector(".menu-toggle");
const nav = document.querySelector(".main-nav");
toggle.addEventListener("click", () => {
  const open = nav.classList.toggle("open");
  toggle.setAttribute("aria-expanded", open);
});
nav.querySelectorAll("a").forEach(a => a.addEventListener("click", () => nav.classList.remove("open")));

document.getElementById("quote-form").addEventListener("submit", async (e) => {
  e.preventDefault();
  const data = Object.fromEntries(new FormData(e.target).entries());
  const message = `ขอใบเสนอราคาจัดเบรก EED Salapao
ชื่อ: ${data.name}
โทร: ${data.phone}
วันที่: ${data.date || "-"}
จำนวน: ${data.quantity || "-"} ชุด
งบต่อชุด: ${data.budget}
รายละเอียด: ${data.details || "-"}`;

  const status = document.getElementById("form-status");
  try {
    await navigator.clipboard.writeText(message);
    status.textContent = "คัดลอกข้อความแล้ว กรุณาส่งให้ร้านผ่าน LINE หรือโทรศัพท์";
  } catch {
    status.textContent = message;
  }

  if (cfg.lineUrl) {
    setTimeout(() => window.open(cfg.lineUrl, "_blank", "noopener"), 500);
  }
});

document.getElementById("year").textContent = new Date().getFullYear();
