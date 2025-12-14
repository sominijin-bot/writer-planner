// annual-goal.module.js
(function () {
  const KEY = "yearVertical";

  const months = Array.from({ length: 12 }, (_, i) => `${i + 1}월`);
  const quarters = ["1분기 (1~3)", "2분기 (4~6)", "3분기 (7~9)", "4분기 (10~12)"];

  const CSS = `
:root {
  --bg:#0f1115;
  --card:#171a21;
  --text:#e6e6eb;
  --muted:#9aa0aa;
  --accent:#7aa2f7;
}
#annual-goal-module, #annual-goal-module * { box-sizing:border-box; }
#annual-goal-module{
  background:var(--bg);
  color:var(--text);
  font-family:system-ui, -apple-system, sans-serif;
  border-radius: 12px;
}
#annual-goal-module header { padding:18px 18px 10px; border-bottom:1px solid #222; }
#annual-goal-module h1 { margin:0 0 6px; font-size:18px; }
#annual-goal-module .total { font-size:13px; color:var(--muted); }

#annual-goal-module .board { overflow-x:auto; padding:16px 18px 18px; }
#annual-goal-module .quarters{
  display:grid;
  grid-template-columns:repeat(12, 260px);
  gap:16px;
  margin-bottom:16px;
}
#annual-goal-module .quarter{
  grid-column:span 3;
  background:#11141a;
  border:1px solid #222;
  border-radius:14px;
  padding:12px;
  text-align:center;
}
#annual-goal-module .quarter input{
  width:100%;
  background:none;
  border:none;
  border-bottom:1px solid #333;
  color:var(--text);
  text-align:center;
  margin-top:6px;
}
#annual-goal-module .columns{
  display:grid;
  grid-template-columns:repeat(12, 260px);
  gap:16px;
}
#annual-goal-module .column{
  background:var(--card);
  border-radius:14px;
  padding:16px;
  display:flex;
  flex-direction:column;
}
#annual-goal-module .column h2{
  margin:0 0 6px;
  text-align:center;
  font-size:16px;
}
#annual-goal-module .progress{
  text-align:center;
  font-size:13px;
  color:var(--muted);
  margin-bottom:12px;
}
#annual-goal-module ul{ list-style:none; padding:0; margin:0; flex:1; }
#annual-goal-module li{
  display:flex;
  gap:6px;
  align-items:center;
  margin-bottom:6px;
}
#annual-goal-module input[type="text"]{
  flex:1;
  background:none;
  border:none;
  border-bottom:1px solid #333;
  color:var(--text);
}
#annual-goal-module input[type="text"]:focus{
  outline:none;
  border-color:var(--accent);
}
#annual-goal-module button{
  background:none;
  border:none;
  color:var(--muted);
  cursor:pointer;
}
#annual-goal-module button:hover{ color:var(--text); }
#annual-goal-module .add{ margin-top:8px; font-size:13px; }
`;

  let hostEl = null;

  function loadState() {
    const raw = localStorage.getItem(KEY);
    if (raw) {
      try { return JSON.parse(raw); } catch (_) {}
    }
    return {
      months: months.map(() => []),
      quarters: quarters.map(() => ({ goal: "" })),
    };
  }

  function saveState(state) {
    localStorage.setItem(KEY, JSON.stringify(state));
  }

  function render(state) {
    if (!hostEl) return;

    hostEl.innerHTML = `
      <style>${CSS}</style>
      <div id="annual-goal-module">
        <header>
          <h1>연간 작업 템플릿</h1>
          <div class="total" id="totalProgress"></div>
        </header>

        <div class="board">
          <div class="quarters" id="quarters"></div>
          <div class="columns" id="months"></div>
        </div>
      </div>
    `;

    const qWrap = hostEl.querySelector("#quarters");
    const mWrap = hostEl.querySelector("#months");
    const totalEl = hostEl.querySelector("#totalProgress");

    let total = 0, doneTotal = 0;

    // quarters
    qWrap.innerHTML = quarters.map((name, i) => `
      <div class="quarter">
        <strong>${name}</strong><br>
        <input data-q="${i}" type="text" placeholder="분기 목표" value="${escapeHtml(state.quarters[i]?.goal || "")}">
      </div>
    `).join("");

    // months
    mWrap.innerHTML = state.months.map((items, mi) => {
      const done = items.filter(x => x.done).length;
      total += items.length;
      doneTotal += done;

      return `
      <div class="column" data-mi="${mi}">
        <h2>${months[mi]}</h2>
        <div class="progress">${items.length ? Math.round(done / items.length * 100) : 0}%</div>
        <ul>
          ${items.map((it, ii) => `
            <li>
              <input data-mi="${mi}" data-ii="${ii}" class="chk" type="checkbox" ${it.done ? "checked" : ""}>
              <input data-mi="${mi}" data-ii="${ii}" class="txt" type="text" value="${escapeHtml(it.text || "")}">
              <button data-mi="${mi}" data-ii="${ii}" class="del" title="삭제">✕</button>
            </li>
          `).join("")}
        </ul>
        <button data-mi="${mi}" class="add">＋ 추가</button>
      </div>`;
    }).join("");

    totalEl.textContent = `전체 달성률 ${total ? Math.round(doneTotal / total * 100) : 0}%`;

    // 이벤트 바인딩 (위임)
    hostEl.addEventListener("input", onInput);
    hostEl.addEventListener("change", onChange);
    hostEl.addEventListener("click", onClick);

    function rerender() {
      saveState(state);
      hostEl.removeEventListener("input", onInput);
      hostEl.removeEventListener("change", onChange);
      hostEl.removeEventListener("click", onClick);
      render(state);
    }

    function onInput(e) {
      const t = e.target;
      if (t.matches("input[data-q]")) {
        const i = Number(t.getAttribute("data-q"));
        state.quarters[i].goal = t.value;
        rerender();
      }
      if (t.matches("input.txt")) {
        const mi = Number(t.getAttribute("data-mi"));
        const ii = Number(t.getAttribute("data-ii"));
        state.months[mi][ii].text = t.value;
        rerender();
      }
    }

    function onChange(e) {
      const t = e.target;
      if (t.matches("input.chk")) {
        const mi = Number(t.getAttribute("data-mi"));
        const ii = Number(t.getAttribute("data-ii"));
        state.months[mi][ii].done = t.checked;
        rerender();
      }
    }

    function onClick(e) {
      const t = e.target;

      if (t.matches("button.add")) {
        const mi = Number(t.getAttribute("data-mi"));
        state.months[mi].push({ text: "", done: false });
        rerender();
      }

      if (t.matches("button.del")) {
        const mi = Number(t.getAttribute("data-mi"));
        const ii = Number(t.getAttribute("data-ii"));
        state.months[mi].splice(ii, 1);
        rerender();
      }
    }
  }

  function escapeHtml(str) {
    return String(str)
      .replaceAll("&", "&amp;")
      .replaceAll("<", "&lt;")
      .replaceAll(">", "&gt;")
      .replaceAll('"', "&quot;")
      .replaceAll("'", "&#039;");
  }

  window.AnnualGoalModule = {
    mount(el) {
      hostEl = el;
      const state = loadState();
      render(state);
    },
    unmount() {
      if (!hostEl) return;
      hostEl.innerHTML = "";
      hostEl = null;
    }
  };
})();
