import { useState, useEffect } from "react";

// 🔗 PASTE YOUR GHL AFFILIATE LINK BELOW
const GHL_AFFILIATE_LINK = "https://www.gohighlevel.com?fp_ref=g5wma&fp_sid=quiz";

// 🔗 PASTE YOUR GHL WEBHOOK URL BELOW TO AUTO-SEND LEADS TO YOUR PIPELINE
const GHL_WEBHOOK_URL = "";

const QUESTIONS = [
  {
    id: "business_type",
    emoji: "🏢",
    question: "What type of business do you run?",
    options: [
      { value: "local_service", icon: "🔧", label: "Local service (salon, gym, contractor, clinic)" },
      { value: "coaching_consulting", icon: "🎓", label: "Coaching or consulting" },
      { value: "real_estate", icon: "🏠", label: "Real estate or mortgage" },
      { value: "ecommerce_retail", icon: "🛍️", label: "E-commerce or retail" },
      { value: "agency_marketing", icon: "📱", label: "Agency or marketing services" },
      { value: "other", icon: "💼", label: "Other / General small business" },
    ],
  },
  {
    id: "biggest_challenge",
    emoji: "🚧",
    question: "What's your #1 growth challenge right now?",
    options: [
      { value: "not_enough_leads", icon: "📉", label: "Not getting enough leads" },
      { value: "leads_falling_through", icon: "🕳️", label: "Leads come in but nothing converts" },
      { value: "no_time", icon: "⏰", label: "Too busy to follow up consistently" },
      { value: "hard_to_book", icon: "📅", label: "Hard to get people to book appointments" },
    ],
  },
  {
    id: "current_tools",
    emoji: "🛠️",
    question: "How are you currently managing leads and customers?",
    options: [
      { value: "spreadsheets", icon: "📊", label: "Spreadsheets or sticky notes" },
      { value: "email_only", icon: "📧", label: "Just email and my phone" },
      { value: "multiple_tools", icon: "🔀", label: "Multiple tools that don't talk to each other" },
      { value: "basic_crm", icon: "💾", label: "A basic CRM but it's not working well" },
    ],
  },
  {
    id: "monthly_leads",
    emoji: "📊",
    question: "How many new leads or inquiries do you get per month?",
    options: [
      { value: "under_20", icon: "🌱", label: "Under 20 — just getting started" },
      { value: "20_to_50", icon: "📈", label: "20–50 — steady but needs work" },
      { value: "50_to_150", icon: "🔥", label: "50–150 — growing fast" },
      { value: "150_plus", icon: "🚀", label: "150+ — volume is the problem" },
    ],
  },
  {
    id: "time_drain",
    emoji: "⏳",
    question: "What's stealing the most time from your week?",
    options: [
      { value: "chasing_leads", icon: "📞", label: "Manually calling and texting leads" },
      { value: "scheduling", icon: "🗓️", label: "Back-and-forth scheduling" },
      { value: "social_reviews", icon: "⭐", label: "Managing reviews and social media" },
      { value: "admin_invoicing", icon: "🧾", label: "Admin, invoicing, and paperwork" },
    ],
  },
];

const SYSTEM_PROMPT = `You are a business automation consultant who specializes in GoHighLevel (GHL). A business owner just completed a short audit quiz. Based on their answers, generate a personalized Business Automation Audit that shows them exactly where they are leaking time and money, and how GoHighLevel solves it.

Be SPECIFIC with dollar amounts and time estimates. Make it feel like a real paid audit. Position GHL as the natural solution without being salesy.

Respond ONLY with a JSON object in this exact format:
{
  "headline": "Personalized headline like 'Your [Business Type] Is Losing Est. $X,XXX/Month to Manual Work'",
  "summary": "2 sentences diagnosing their specific situation based on their answers",
  "monthly_loss": "Estimated monthly revenue/time loss in dollars (be specific, e.g. '$2,400–$4,800/mo')",
  "hours_lost": "Estimated hours lost per week to manual work (e.g. '8–12 hrs/week')",
  "top_leak": "Their single biggest problem in one punchy sentence",
  "leaks": [
    { "title": "Leak title", "detail": "1 sentence explaining the specific problem and cost", "fix": "Which specific GHL feature fixes this (e.g. 'GHL Automated Follow-Up Sequences')" },
    { "title": "Leak title", "detail": "1 sentence explaining the specific problem and cost", "fix": "Which specific GHL feature fixes this" },
    { "title": "Leak title", "detail": "1 sentence explaining the specific problem and cost", "fix": "Which specific GHL feature fixes this" }
  ],
  "quick_wins": ["Quick win 1 they could implement in week 1", "Quick win 2", "Quick win 3"],
  "ghl_features": ["GHL Feature 1 most relevant to them", "Feature 2", "Feature 3", "Feature 4"],
  "roi_estimate": "Realistic ROI estimate if they fix these leaks (e.g. 'Businesses like yours typically recover $3,000–$6,000/month within 60 days of automating follow-up')",
  "cta_line": "One compelling sentence urging them to try GHL free (e.g. 'Start your free 14-day GoHighLevel trial and plug these leaks this week')"
}`;

export default function App() {
  const [screen, setScreen] = useState("landing");
  const [currentQ, setCurrentQ] = useState(0);
  const [answers, setAnswers] = useState({});
  const [selected, setSelected] = useState(null);
  const [lead, setLead] = useState({ name: "", email: "", business: "" });
  const [leads, setLeads] = useState([]);
  const [gateError, setGateError] = useState("");
  const [plan, setPlan] = useState(null);
  const [apiError, setApiError] = useState("");

  function handleStart() {
    setScreen("quiz"); setCurrentQ(0); setAnswers({}); setSelected(null);
  }

  function handleSelect(value) { setSelected(value); }

  function handleNext() {
    if (!selected) return;
    const newAnswers = { ...answers, [QUESTIONS[currentQ].id]: selected };
    setAnswers(newAnswers);
    setSelected(null);
    if (currentQ < QUESTIONS.length - 1) setCurrentQ(currentQ + 1);
    else setScreen("gate");
  }

  function handleGateSubmit() {
    if (!lead.name.trim()) { setGateError("Please enter your first name."); return; }
    if (!lead.email.trim() || !lead.email.includes("@")) { setGateError("Please enter a valid email."); return; }
    if (!lead.business.trim()) { setGateError("Please enter your business name."); return; }
    setGateError("");
    const newLead = { ...lead, answers, timestamp: new Date().toISOString() };
    setLeads(prev => [...prev, newLead]);
    if (GHL_WEBHOOK_URL) {
      fetch(GHL_WEBHOOK_URL, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(newLead),
      }).catch(() => {});
    }
    setScreen("loading");
    generatePlan(answers, lead);
  }

  async function generatePlan(finalAnswers, leadInfo) {
    try {
      const res = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          model: "claude-sonnet-4-20250514",
          max_tokens: 1200,
          system: SYSTEM_PROMPT,
          messages: [{
            role: "user",
            content: `Business owner audit answers:
- Business type: ${finalAnswers.business_type}
- Biggest challenge: ${finalAnswers.biggest_challenge}
- Current tools: ${finalAnswers.current_tools}
- Monthly leads: ${finalAnswers.monthly_leads}
- Biggest time drain: ${finalAnswers.time_drain}
- Business name: ${leadInfo.business}

Generate their personalized Business Automation Audit.`
          }],
        }),
      });
      const data = await res.json();
      const text = data.content.map(b => b.text || "").join("");
      const parsed = JSON.parse(text.replace(/```json|```/g, "").trim());
      setPlan(parsed);
      setScreen("result");
    } catch (e) {
      setApiError("Something went wrong. Please try again.");
      setScreen("gate");
    }
  }

  function handleRetake() {
    setScreen("landing"); setPlan(null); setAnswers({}); setCurrentQ(0);
    setSelected(null); setLead({ name: "", email: "", business: "" });
    setGateError(""); setApiError("");
  }

  return (
    <>
      <style>{`
        @keyframes spin { to { transform: rotate(360deg); } }
        @keyframes fadeUp { from { opacity:0; transform:translateY(14px); } to { opacity:1; transform:translateY(0); } }
        * { box-sizing: border-box; }
        input::placeholder { color: #5A5550; }
      `}</style>
      <div style={S.root}>
        <div style={S.bg} />
        {screen === "landing" && <Landing onStart={handleStart} />}
        {screen === "quiz"    && <Quiz question={QUESTIONS[currentQ]} questionIndex={currentQ} total={QUESTIONS.length} selected={selected} onSelect={handleSelect} onNext={handleNext} />}
        {screen === "gate"    && <EmailGate lead={lead} setLead={setLead} onSubmit={handleGateSubmit} error={gateError || apiError} />}
        {screen === "loading" && <Loading />}
        {screen === "result"  && plan && <Result plan={plan} onRetake={handleRetake} leads={leads} leadName={lead.name} />}
      </div>
    </>
  );
}

function Landing({ onStart }) {
  return (
    <div style={S.screen}>
      <div style={{ ...S.col, maxWidth: 560, alignItems: "center", textAlign: "center", gap: 20, animation: "fadeUp .6s ease" }}>
        <div style={S.badge}>FREE BUSINESS AUDIT · 2 MINUTES</div>
        <h1 style={{ fontSize: "clamp(2rem,6vw,3.2rem)", fontWeight: 400, lineHeight: 1.12, margin: 0, letterSpacing: "-.02em", color: "#F0EDE8" }}>
          Is Your Business<br /><span style={{ color: "#FF6B35", fontStyle: "italic" }}>Leaking Revenue?</span>
        </h1>
        <p style={{ fontSize: ".97rem", color: "#A09C96", lineHeight: 1.75, margin: 0, maxWidth: 440 }}>
          Answer 5 questions and get a free personalized audit showing exactly where your business is losing time and money — and how to fix it.
        </p>
        <div style={{ display: "flex", gap: "1.5rem", justifyContent: "center", padding: "1rem 2rem", background: "#FFFFFF08", borderRadius: 16, border: "1px solid #FFFFFF10", width: "100%" }}>
          {[["5","Questions"],["Free","Audit"],["Instant","Results"]].map(([n,l]) => (
            <div key={l} style={{ display: "flex", flexDirection: "column", alignItems: "center", gap: 3 }}>
              <span style={{ fontSize: "1.3rem", fontWeight: 500, color: "#FF6B35", fontFamily: "monospace" }}>{n}</span>
              <span style={{ fontSize: ".66rem", color: "#6B6864", letterSpacing: ".1em", textTransform: "uppercase", fontFamily: "monospace" }}>{l}</span>
            </div>
          ))}
        </div>
        <div style={{ display: "flex", flexDirection: "column", gap: 8, width: "100%", maxWidth: 400 }}>
          {["Stop losing leads to slow follow-up", "See exactly which tasks to automate first", "Get a personalized automation roadmap"].map(p => (
            <div key={p} style={{ display: "flex", alignItems: "center", gap: 10, fontSize: ".88rem", color: "#C0BCB6" }}>
              <span style={{ color: "#FF6B35", fontSize: "1rem" }}>✓</span>{p}
            </div>
          ))}
        </div>
        <button style={S.ctaBtn} onClick={onStart}>Get My Free Audit →</button>
        <p style={{ fontSize: ".72rem", color: "#4A4844", fontFamily: "monospace", margin: 0 }}>No credit card. No commitment. 100% free.</p>
      </div>
    </div>
  );
}

function Quiz({ question, questionIndex, total, selected, onSelect, onNext }) {
  const isLast = questionIndex === total - 1;
  return (
    <div style={S.screen}>
      <div style={{ ...S.col, maxWidth: 560, gap: 18, animation: "fadeUp .4s ease" }}>
        <div style={{ display: "flex", alignItems: "center", gap: 12 }}>
          <div style={{ flex: 1, height: 3, background: "#FFFFFF10", borderRadius: 99, overflow: "hidden" }}>
            <div style={{ height: "100%", background: "#FF6B35", borderRadius: 99, width: `${(questionIndex / total) * 100}%`, transition: "width .4s ease" }} />
          </div>
          <span style={{ fontSize: ".72rem", color: "#6B6864", fontFamily: "monospace", whiteSpace: "nowrap" }}>{questionIndex + 1} / {total}</span>
        </div>
        <div style={{ fontSize: "2.2rem", lineHeight: 1 }}>{question.emoji}</div>
        <h2 style={{ fontSize: "clamp(1.3rem,3.5vw,1.8rem)", fontWeight: 400, margin: 0, lineHeight: 1.25, letterSpacing: "-.02em", color: "#F0EDE8" }}>{question.question}</h2>
        <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 10 }}>
          {question.options.map(opt => (
            <button key={opt.value} onClick={() => onSelect(opt.value)} style={{
              display: "flex", flexDirection: "column", gap: 7, padding: ".9rem",
              background: selected === opt.value ? "#FF6B3518" : "#FFFFFF06",
              border: selected === opt.value ? "1px solid #FF6B3570" : "1px solid #FFFFFF12",
              borderRadius: 12, cursor: "pointer", textAlign: "left",
              color: selected === opt.value ? "#F0EDE8" : "#C0BCB6",
              fontFamily: "inherit", transition: "all .15s",
            }}>
              <span style={{ fontSize: "1.3rem" }}>{opt.icon}</span>
              <span style={{ fontSize: ".82rem", lineHeight: 1.3, fontFamily: "monospace" }}>{opt.label}</span>
            </button>
          ))}
        </div>
        <button onClick={onNext} disabled={!selected} style={{ ...S.ctaBtn, opacity: selected ? 1 : 0.35, cursor: selected ? "pointer" : "not-allowed" }}>
          {isLast ? "Show My Audit →" : "Next →"}
        </button>
      </div>
    </div>
  );
}

function EmailGate({ lead, setLead, onSubmit, error }) {
  return (
    <div style={S.screen}>
      <div style={{ ...S.col, maxWidth: 420, alignItems: "center", textAlign: "center", gap: 18, animation: "fadeUp .5s ease" }}>
        <div style={{ fontSize: "2.8rem" }}>📋</div>
        <h2 style={{ fontSize: "1.9rem", fontWeight: 400, margin: 0, letterSpacing: "-.02em", color: "#F0EDE8" }}>Your audit is ready.</h2>
        <p style={{ fontSize: ".93rem", color: "#A09C96", lineHeight: 1.65, margin: 0 }}>
          Where should we send your personalized Business Automation Report?
        </p>
        <div style={{ ...S.col, gap: 9, width: "100%" }}>
          <input style={S.input} type="text" placeholder="Your first name" value={lead.name} onChange={e => setLead(l => ({ ...l, name: e.target.value }))} />
          <input style={S.input} type="text" placeholder="Business name" value={lead.business} onChange={e => setLead(l => ({ ...l, business: e.target.value }))} />
          <input style={S.input} type="email" placeholder="Email address" value={lead.email} onChange={e => setLead(l => ({ ...l, email: e.target.value }))} />
          {error && <div style={{ padding: ".6rem .9rem", background: "#FF444415", border: "1px solid #FF444440", borderRadius: 8, fontSize: ".82rem", color: "#FF8888", fontFamily: "monospace" }}>{error}</div>}
          <button style={S.ctaBtn} onClick={onSubmit}>Unlock My Audit →</button>
        </div>
        <p style={{ fontSize: ".72rem", color: "#4A4844", margin: 0, fontFamily: "monospace" }}>No spam. Unsubscribe anytime. Results are instant.</p>
      </div>
    </div>
  );
}

function Loading() {
  const steps = ["Analyzing your business profile…", "Calculating revenue leaks…", "Identifying automation opportunities…", "Building your custom audit…"];
  const [step, setStep] = useState(0);
  useEffect(() => {
    const t = setInterval(() => setStep(s => Math.min(s + 1, steps.length - 1)), 950);
    return () => clearInterval(t);
  }, []);
  return (
    <div style={{ ...S.screen, justifyContent: "center" }}>
      <div style={{ ...S.col, alignItems: "center", textAlign: "center", gap: 22, maxWidth: 300 }}>
        <div style={{ width: 44, height: 44, border: "3px solid #FFFFFF10", borderTop: "3px solid #FF6B35", borderRadius: "50%", animation: "spin 1s linear infinite" }} />
        <h2 style={{ fontSize: "1.3rem", fontWeight: 400, margin: 0, letterSpacing: "-.02em", color: "#F0EDE8" }}>Running Your Audit</h2>
        <div style={{ ...S.col, gap: 7, width: "100%", textAlign: "left" }}>
          {steps.map((st, i) => (
            <div key={st} style={{ fontSize: ".82rem", color: i <= step ? "#A09C96" : "#2A2826", fontFamily: "monospace", transition: "color .4s" }}>
              <span style={{ color: "#FF6B35", marginRight: 7 }}>{i <= step ? "✓" : "○"}</span>{st}
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}

function Result({ plan, onRetake, leads, leadName }) {
  return (
    <div style={{ minHeight: "100vh", padding: "2rem 1.25rem", display: "flex", justifyContent: "center", position: "relative", zIndex: 1 }}>
      <div style={{ ...S.col, maxWidth: 600, width: "100%", gap: 16, paddingBottom: "3rem", animation: "fadeUp .5s ease" }}>

        {/* Header */}
        <div style={{ ...S.col, alignItems: "center", textAlign: "center", gap: 10, paddingTop: "1rem" }}>
          <div style={S.badge}>📋 YOUR BUSINESS AUDIT RESULTS</div>
          <h1 style={{ fontSize: "clamp(1.6rem,4.5vw,2.4rem)", fontWeight: 400, margin: 0, lineHeight: 1.2, letterSpacing: "-.02em", color: "#F0EDE8" }}>{plan.headline}</h1>
          <p style={{ fontSize: ".93rem", color: "#A09C96", margin: 0, lineHeight: 1.65 }}>{plan.summary}</p>
        </div>

        {/* Loss Stats */}
        <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 12 }}>
          <div style={{ padding: "1.1rem", background: "#FF6B3512", border: "1px solid #FF6B3530", borderRadius: 14, display: "flex", flexDirection: "column", gap: 4, alignItems: "center", textAlign: "center" }}>
            <span style={{ fontSize: ".62rem", letterSpacing: ".15em", textTransform: "uppercase", color: "#FF6B35", fontFamily: "monospace" }}>Estimated Monthly Loss</span>
            <span style={{ fontSize: "1.8rem", fontWeight: 500, color: "#FF6B35", fontFamily: "monospace" }}>{plan.monthly_loss}</span>
          </div>
          <div style={{ padding: "1.1rem", background: "#FFFFFF06", border: "1px solid #FFFFFF10", borderRadius: 14, display: "flex", flexDirection: "column", gap: 4, alignItems: "center", textAlign: "center" }}>
            <span style={{ fontSize: ".62rem", letterSpacing: ".15em", textTransform: "uppercase", color: "#6B6864", fontFamily: "monospace" }}>Hours Lost Per Week</span>
            <span style={{ fontSize: "1.8rem", fontWeight: 500, color: "#F0EDE8", fontFamily: "monospace" }}>{plan.hours_lost}</span>
          </div>
        </div>

        {/* Top Leak */}
        <div style={{ padding: "1rem 1.15rem", background: "#FF6B3510", border: "1px solid #FF6B3530", borderRadius: 12 }}>
          <span style={{ fontSize: ".62rem", letterSpacing: ".15em", textTransform: "uppercase", color: "#FF6B35", fontFamily: "monospace" }}>🚨 Biggest Leak</span>
          <p style={{ margin: ".4rem 0 0", fontSize: "1rem", color: "#F0EDE8", lineHeight: 1.5, fontStyle: "italic" }}>{plan.top_leak}</p>
        </div>

        {/* Revenue Leaks */}
        <div style={{ fontSize: ".62rem", letterSpacing: ".2em", textTransform: "uppercase", color: "#4A4844", fontFamily: "monospace", paddingTop: 4 }}>Where You're Losing Money</div>
        {plan.leaks.map((leak, i) => (
          <div key={i} style={{ padding: "1.1rem 1.15rem", background: "#FFFFFF06", border: "1px solid #FFFFFF10", borderRadius: 14, display: "flex", flexDirection: "column", gap: 6 }}>
            <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", gap: 10 }}>
              <span style={{ fontSize: ".95rem", fontWeight: 500, color: "#F0EDE8" }}>{leak.title}</span>
              <span style={{ fontSize: ".7rem", padding: ".25rem .65rem", background: "#FF6B3515", border: "1px solid #FF6B3530", borderRadius: 99, color: "#FF6B35", fontFamily: "monospace", whiteSpace: "nowrap", flexShrink: 0 }}>Leak #{i + 1}</span>
            </div>
            <p style={{ margin: 0, fontSize: ".84rem", color: "#A09C96", lineHeight: 1.5 }}>{leak.detail}</p>
            <div style={{ display: "flex", alignItems: "center", gap: 7, fontSize: ".78rem", color: "#10B981", fontFamily: "monospace" }}>
              <span>✓ Fix:</span><span>{leak.fix}</span>
            </div>
          </div>
        ))}

        {/* Quick Wins */}
        <div style={{ padding: "1.1rem 1.15rem", background: "#10B98112", border: "1px solid #10B98130", borderRadius: 14 }}>
          <div style={{ fontSize: ".62rem", letterSpacing: ".15em", textTransform: "uppercase", color: "#10B981", fontFamily: "monospace", marginBottom: 10 }}>⚡ Quick Wins — Implement This Week</div>
          {plan.quick_wins.map((w, i) => (
            <div key={i} style={{ display: "flex", gap: 8, fontSize: ".85rem", color: "#C0BCB6", lineHeight: 1.45, marginBottom: 7 }}>
              <span style={{ color: "#10B981", flexShrink: 0 }}>→</span>{w}
            </div>
          ))}
        </div>

        {/* GHL Features */}
        <div style={{ padding: "1.1rem 1.15rem", background: "#FFFFFF06", border: "1px solid #FFFFFF10", borderRadius: 14 }}>
          <div style={{ fontSize: ".62rem", letterSpacing: ".15em", textTransform: "uppercase", color: "#6B6864", fontFamily: "monospace", marginBottom: 8 }}>🛠️ GHL Features That Solve This</div>
          <div style={{ display: "flex", flexWrap: "wrap", gap: 7 }}>
            {plan.ghl_features.map(f => (
              <span key={f} style={{ padding: ".3rem .75rem", background: "#6366F115", border: "1px solid #6366F130", borderRadius: 99, fontSize: ".78rem", color: "#A5B4FC", fontFamily: "monospace" }}>{f}</span>
            ))}
          </div>
        </div>

        {/* ROI */}
        <div style={{ padding: "1.1rem 1.15rem", background: "#F59E0B10", border: "1px solid #F59E0B30", borderRadius: 14 }}>
          <div style={{ fontSize: ".62rem", letterSpacing: ".15em", textTransform: "uppercase", color: "#F59E0B", fontFamily: "monospace", marginBottom: 6 }}>💰 Your ROI Potential</div>
          <p style={{ margin: 0, fontSize: ".93rem", color: "#F0EDE8", lineHeight: 1.6 }}>{plan.roi_estimate}</p>
        </div>

        {/* CTA */}
        <div style={{ padding: "1.5rem", background: "linear-gradient(135deg, #FF6B3520 0%, #FF6B3508 100%)", border: "1px solid #FF6B3540", borderRadius: 16, display: "flex", flexDirection: "column", gap: 12, alignItems: "center", textAlign: "center" }}>
          <h3 style={{ fontSize: "1.2rem", fontWeight: 400, margin: 0, color: "#F0EDE8", lineHeight: 1.3 }}>{plan.cta_line}</h3>
          <p style={{ fontSize: ".85rem", color: "#A09C96", margin: 0 }}>14-day free trial · No credit card required · Cancel anytime</p>
          <a href={GHL_AFFILIATE_LINK} target="_blank" rel="noopener noreferrer" style={{ padding: ".9rem 2.2rem", background: "#FF6B35", color: "#fff", border: "none", borderRadius: 12, fontSize: "1rem", fontWeight: 600, cursor: "pointer", textDecoration: "none", display: "inline-block", letterSpacing: "-.01em", boxShadow: "0 8px 32px #FF6B3540" }}>
            Start My Free 14-Day Trial →
          </a>
          <p style={{ fontSize: ".72rem", color: "#4A4844", margin: 0, fontFamily: "monospace" }}>Trusted by 60,000+ businesses worldwide</p>
        </div>

        <button onClick={onRetake} style={{ padding: ".7rem 1.5rem", background: "transparent", border: "1px solid #FFFFFF18", borderRadius: 10, color: "#6B6864", fontFamily: "monospace", fontSize: ".83rem", cursor: "pointer", alignSelf: "center" }}>
          ↩ Start Over
        </button>

        {/* Leads Panel */}
        {leads && leads.length > 0 && (
          <div style={{ padding: "1.1rem", background: "#10B98110", border: "1px solid #10B98128", borderRadius: 14, display: "flex", flexDirection: "column", gap: 9, marginTop: 8 }}>
            <div style={{ fontSize: ".65rem", letterSpacing: ".12em", textTransform: "uppercase", color: "#10B981", fontFamily: "monospace", fontWeight: 700 }}>📋 Leads Captured ({leads.length})</div>
            <p style={{ fontSize: ".75rem", color: "#6B9E8A", margin: 0, fontFamily: "monospace" }}>These auto-fire to your GHL pipeline once your webhook is connected.</p>
            {leads.map((l, i) => (
              <div key={i} style={{ display: "flex", gap: 10, alignItems: "center", padding: ".45rem 0", borderTop: "1px solid #FFFFFF08", flexWrap: "wrap" }}>
                <span style={{ fontSize: ".82rem", color: "#F0EDE8", fontFamily: "monospace", minWidth: 80 }}>{l.name}</span>
                <span style={{ fontSize: ".82rem", color: "#10B981", fontFamily: "monospace", flex: 1 }}>{l.email}</span>
                <span style={{ fontSize: ".72rem", color: "#4A4844", fontFamily: "monospace" }}>{l.business}</span>
              </div>
            ))}
          </div>
        )}

      </div>
    </div>
  );
}

const S = {
  root: { minHeight: "100vh", background: "#0C0C12", color: "#F0EDE8", fontFamily: "'Georgia','Times New Roman',serif", position: "relative", overflow: "hidden" },
  bg: { position: "fixed", inset: 0, background: "radial-gradient(ellipse 80% 50% at 50% -10%, #FF6B3510 0%, transparent 70%)", pointerEvents: "none", zIndex: 0 },
  screen: { minHeight: "100vh", display: "flex", flexDirection: "column", alignItems: "center", justifyContent: "center", padding: "2rem 1.25rem", position: "relative", zIndex: 1 },
  col: { display: "flex", flexDirection: "column", width: "100%" },
  badge: { display: "inline-block", padding: ".3rem .9rem", background: "#FF6B3520", border: "1px solid #FF6B3550", borderRadius: 100, fontSize: ".66rem", letterSpacing: ".13em", color: "#FF6B35", fontFamily: "monospace" },
  ctaBtn: { padding: ".9rem 2.2rem", background: "#FF6B35", color: "#fff", border: "none", borderRadius: 12, fontSize: "1rem", fontWeight: 600, cursor: "pointer", fontFamily: "inherit", boxShadow: "0 8px 32px #FF6B3540" },
  input: { padding: ".85rem 1rem", background: "#FFFFFF08", border: "1px solid #FFFFFF18", borderRadius: 10, color: "#F0EDE8", fontFamily: "monospace", fontSize: ".92rem", outline: "none", width: "100%" },
};
