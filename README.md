<h1 align="center">AI-Powered Customer Feedback Automation (n8n)</h1>

<p align="center">
An end-to-end AI-powered workflow that automatically classifies, stores, routes, and responds to customer feedback using n8n and a local LLM.
</p>

<hr/>

<h2> Problem Statement</h2>
<p>
Customer feedback typically arrives as unstructured text, making it difficult to manually
categorize, route, track, and respond in a timely manner.
This often leads to delays, inconsistent handling, and increased operational overhead for support and product teams.
</p>

<h2> Solution</h2>
<p>
This project implements a fully automated customer feedback handling system using <b>n8n</b>.
Incoming feedback is classified using an AI agent and automatically routed to the appropriate internal team
with real-time notifications and customer acknowledgments.
</p>

<hr/>

<h2> Workflow Overview</h2>

<h3>Customer Feedback Form</h3>
<p>
Customers submit feedback using an n8n-powered form containing basic contact information and free-text feedback.
</p>
<img src="assets/images/Screenshot 2026-01-18 200430.png" width="800"/>

<h3>AI-Based Feedback Classification</h3>
<p>
A local LLM (Ollama + Phi-3 Mini) analyzes the feedback text and assigns exactly one category using
strict prompt-based rules:
</p>
<ul>
  <li><b>Complain</b> – Bug reports, performance issues, negative experiences</li>
  <li><b>Compliment</b> – Positive feedback or appreciation</li>
  <li><b>Feature Addition Request</b> – Suggestions or product improvement ideas</li>
</ul>
<p>
The AI is constrained to output only one predefined label, ensuring consistent and reliable automation.
</p>
<img src="assets/images/Screenshot 2026-01-18 202921.png" width="800"/>

<h3>End-to-End n8n Workflow</h3>
<p>
Form data and AI classification output are merged and passed through a rule-based router,
which directs the feedback to the correct automation path.
</p>
<img src="assets/images/Screenshot 2026-01-18 200457.png" width="900"/>

<h3>Team Notification via Slack</h3>
<p>
Based on the classified category, feedback is automatically sent to the relevant internal Slack channel:
</p>
<ul>
  <li><b>Complain</b> → Bug / Support team channel</li>
  <li><b>Feature Addition Request</b> → Product or Feature planning team channel</li>
  <li><b>Compliment</b> → General or customer success team channel</li>
</ul>
<p>
This ensures that issues reach the correct team instantly without manual triaging.
</p>
<img src="assets/images/Screenshot 2026-01-18 203513.png" width="900"/>

<h3>Automated Customer Email Response</h3>
<p>
An acknowledgment email is automatically sent to the customer based on the feedback category,
confirming receipt and setting appropriate expectations.
</p>
<img src="assets/images/Screenshot 2026-01-18 202858.png" width="900"/>

<h3>Structured Storage in Airtable</h3>
<p>
All feedback is stored in Airtable with structured fields, enabling tracking, filtering,
and future analysis by category.
</p>
<img src="assets/images/Screenshot 2026-01-18 205331.png" width="900"/>

<hr/>

<h2> Key Learnings</h2>
<ul>
  <li>Controlling AI outputs using strict prompt design</li>
  <li>Using AI as a reliable component inside automation pipelines</li>
  <li>Designing complete end-to-end workflows instead of isolated demos</li>
  <li>Automating feedback routing for both bug resolution and feature planning</li>
  <li>Applying AI to realistic business workflows</li>
</ul>

<hr/>

<h2> Tech Stack</h2>
<ul>
  <li><b>n8n</b> – Workflow automation</li>
  <li><b>Ollama</b> – Local LLM runtime</li>
  <li><b>Phi-3 Mini</b> – AI text classification</li>
  <li><b>Airtable</b> – Structured data storage</li>
  <li><b>Slack</b> – Team-based real-time notifications</li>
  <li><b>Gmail (SMTP)</b> – Automated email responses</li>
</ul>

<hr/>

<h2> Repository Structure</h2>

<pre>
n8n-customer-feedback/
│
├── assets/
│   └── images/
│
├── ai-customer-feedback-automation-n8n.json
│
├── README.md
</pre>

<hr/>

<h2> Notes</h2>
<ul>
  <li>API keys and credentials are not included in this repository</li>
  <li>Users must configure their own credentials within n8n</li>
  <li>This project focuses on automation, reliability, and explainability rather than model training</li>
</ul>

<hr/>

<h2> Why This Project Matters</h2>
<p>
This project demonstrates practical AI usage beyond demos by combining automation,
prompt engineering, and system design to solve a real-world business problem.
It highlights how AI can be safely integrated into production workflows without replacing human decision-making.
</p>
