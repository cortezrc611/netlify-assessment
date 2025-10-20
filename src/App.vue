<template>
  <div class="container">
    <header class="header">
      <h1>Netlify Developer Assessment – FAQ</h1>
      <p>Built with Vue.js, TypeScript & CSS</p>
    </header>

    <section class="faq-section">
      <div
        v-for="(faq, index) in faqs"
        :key="index"
        class="faq-item"
      >
        <button @click="toggle(index)" class="faq-question">
          <span class="faq-title">{{ faq.title }}</span>
          <span
            class="arrow"
            :class="{ open: faq.open }"
          >
            ▼
          </span>
        </button>

        <transition name="fade">
          <div v-show="faq.open" class="faq-answer">
            <div v-html="faq.content"></div>
          </div>
        </transition>
      </div>
    </section>

    <footer class="footer">
      © 2025 Netlify Assessment by RC Cortez
    </footer>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";

interface FAQ {
  title: string;
  content: string;
  open: boolean;
}

const faqs = ref<FAQ[]>([
  {
    title: "1. Project Overview",
    content: `
      <p>I built this Netlify assessment website using <strong>Vue.js, TypeScript, and CSS</strong>.
      I chose these tools for their efficiency, type safety, and ease of creating responsive designs.</p>
      <p>Instead of using an API, I defined a static product list to focus on layout and functionality.
      One challenge I faced was ensuring the grid layout remained responsive, which I solved with
      <strong>flexbox and media queries</strong>.</p>
    `,
    open: true,
  },
  {
    title: "2. Netlify Experience",
    content: `
      <p>The deployment process was fast, and the interface intuitive.
      Adding more detailed error logs or clearer feedback could make troubleshooting even easier.</p>
    `,
    open: false,
  },
  {
    title: "3. Favorite Activities",
    content: `
      <ul>
        <li>Setting up site frameworks for debugging</li>
        <li>Collaborating on new features</li>
        <li>Developing code examples for customers</li>
        <li>Submitting bug reports and fixes</li>
        <li>Helping train and onboard new teammates</li>
      </ul>
    `,
    open: false,
  },
  {
    title: "4. Least Favorite Activities",
    content: `
      <ul>
        <li>Responding to 20+ support emails daily</li>
        <li>Creating video tutorials</li>
        <li>Debugging unfamiliar frameworks</li>
        <li>Joining Zoom calls with VIP customers</li>
        <li>Managing a Support team</li>
      </ul>
    `,
    open: false,
  },
  {
    title: "5. API Documentation Example",
    content: `
      <p>I think <a href='https://docs.stripe.com/apis' target='_blank'>Stripe’s API documentation</a>
      is exceptionally well done — clear, well-structured, and developer-friendly with interactive examples.</p>
    `,
    open: false,
  },
  {
    title: "6. DNS Configuration Challenges",
    content: `
      <p>Concepts like <strong>A records</strong>, <strong>CNAMEs</strong>, and <strong>nameservers</strong>
      can be confusing. Propagation delays also make troubleshooting difficult, as changes aren't immediate.</p>
    `,
    open: false,
  },
  {
    title: "7. Troubleshooting a Build Error",
    content: `
      <p>I’d review the build logs before the “exit code: 2” message, check the build command and environment variables,
      and confirm if the project builds locally to narrow down the issue.</p>
    `,
    open: false,
  },
  {
    title: "8. Example 301 Redirect",
    content: `
      <pre>/netlify/:query  https://www.google.com/search?q=:query  301</pre>
      <p><code>/netlify/:query</code> captures anything after it as a parameter, passed to Google as a search term using a <strong>301</strong> redirect.</p>
    `,
    open: false,
  },
  {
    title: "9. Security Report Handling",
    content: `
      <p>If I received a report about a severe security issue, I’d acknowledge it immediately, thank the reporter,
      and ensure it’s forwarded to the proper team while keeping communication open and respectful.</p>
    `,
    open: false,
  },

]);

const toggle = (index: number) => {
  const item = faqs.value[index];
  if (!item) return;
  item.open = !item.open;
};
</script>

<style scoped>
/* Layout */
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 40px 20px;
  font-family: "Segoe UI", Roboto, sans-serif;
  color: #333;
}

/* Header */
.header {
  text-align: center;
  margin-bottom: 40px;
}
.header h1 {
  font-size: 2rem;
  color: #1e40af;
  margin-bottom: 8px;
}
.header p {
  color: #666;
}

/* FAQ Section */
.faq-section {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.faq-item {
  border: 1px solid #ddd;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 1px 3px rgba(0,0,0,0.05);
}

/* Question Button */
.faq-question {
  background-color: #f8f8f8;
  border: none;
  padding: 16px 20px;
  width: 100%;
  text-align: left;
  font-size: 1rem;
  font-weight: 600;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #1e40af;
  cursor: pointer;
  transition: background 0.2s ease;
}
.faq-question:hover {
  background-color: #f0f0f0;
}
.faq-question:focus {
  outline: none;
}

/* Answer Section */
.faq-answer {
  background: #fff;
  padding: 0 20px 20px;
  line-height: 1.6;
  color: #444;
}
.faq-answer ul {
  margin: 8px 0;
  padding-left: 20px;
}
.faq-answer li {
  margin-bottom: 4px;
}
.faq-answer a {
  color: #2563eb;
  text-decoration: none;
}
.faq-answer a:hover {
  text-decoration: underline;
}

/* Arrow rotation */
.arrow {
  font-size: 1.2rem;
  color: #555;
  transition: transform 0.3s ease;
}
.arrow.open {
  transform: rotate(180deg);
}

/* Code block */
pre {
  background-color: #f4f4f4;
  border-left: 4px solid #3b82f6;
  padding: 10px;
  border-radius: 6px;
  font-size: 0.9rem;
  font-family: "Fira Code", monospace;
  overflow-x: auto;
}

/* Footer */
.footer {
  text-align: center;
  margin-top: 40px;
  color: #888;
  font-size: 0.9rem;
}

/* Fade animation */
.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-5px);
}

/* Responsive */
@media (max-width: 600px) {
  .header h1 {
    font-size: 1.6rem;
  }
  .faq-question {
    font-size: 0.95rem;
  }
}
</style>
