<template>
  <div class="rv">
    <h1 class="name-highlight">Chawagorn Chomtaworn</h1>

    <div class="contact-vert contact-highlight">
      <div>065-815-1663</div>
      <div>jamemech01@gmail.com</div>
      <div><a href="https://github.com/jamemech01" target="_blank">github.com/jamemech01</a></div>
    </div>

    <p class="role">
      <em>
        Backend developer focused on NestJS and Node.js. Experienced in RESTful API design, authentication, and database integration. Passionate about clean architecture, scalable systems, and continuously improving code quality.
      </em>
    </p>

    <section>
      <h2>Experience</h2>
      <div v-for="job in experience" :key="job.title + job.company" class="exp-row">
        <div class="exp-left">
          <span class="entry-title">{{ job.title }}</span>
          <span class="entry-meta">{{ job.company }}</span>
          <span class="entry-date">{{ job.date }}</span>
        </div>
        <div class="exp-right">
          <div v-for="item in job.items" :key="item" class="exp-bullet">
            <div class="bullet-dot"></div>
            <span>{{ item }}</span>
          </div>
        </div>
      </div>
    </section>

    <section>
      <h2>Education</h2>
      <p class="edu-text">
        B.Sc. Mathematics — King Mongkut's University of Technology Thonburi (2012–2015)
      </p>
    </section>

    <section>
      <h2>Projects</h2>
      <div v-for="proj in projects" :key="proj.title" class="proj-card">
        <div class="proj-header">
          <span class="entry-title">{{ proj.title }}</span>
          <a class="proj-url" :href="proj.url" target="_blank">{{ proj.urlLabel }}</a>
        </div>
        <p class="proj-desc">{{ proj.desc }}</p>
      </div>
    </section>

    <section>
      <h2>Skills</h2>
      <div class="skills">
        <div v-for="row in skills" :key="row.key" class="skill-row">
          <span class="skill-key">{{ row.key }}</span>
          <span v-for="tag in row.tags" :key="tag" class="skill-tag">{{ tag }}</span>
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

interface Job {
  title: string
  company: string
  date: string
  items: string[]
}

interface Project {
  title: string
  url: string
  urlLabel: string
  desc: string
}

interface SkillRow {
  key: string
  tags: string[]
}

export default defineComponent({
  name: 'App',
  setup() {
    const experience: Job[] = [
      {
        title: 'Software Developer',
        company: 'Thai Smile Bus',
        date: 'Sep – Nov 2025',
        items: [
          'Built internal web application covering news, personnel, and general company pages',
          'Built a GPS platform for vehicle rental clients with an admin dashboard for fleet monitoring',
        ],
      },
      {
        title: 'Production Planner',
        company: 'Thai Benkan',
        date: '2021 – 2024',
        items: [
          'Managed production planning using data analysis to meet delivery targets',
          'Developed Excel-based tools to automate production data extraction and analysis',
        ],
      },
      {
        title: 'Software Support',
        company: 'SF Corporation',
        date: '2019 – 2020',
        items: [
          'Tested application features and verified functionality before each release',
          'Investigated and resolved transaction issues reported by branches using SQL queries',
        ],
      },
      {
        title: 'Business Development',
        company: 'Bow Bakery House',
        date: '2017 – 2018',
        items: [
          'Designed new product concepts and packaging to expand the product line',
          'Coordinated client customization requests between customers and the production team',
        ],
      },
    ]

    const projects: Project[] = [
      {
        title: 'World Market (Claude AI)',
        url: 'https://github.com/jamemech01/world-market-claude',
        urlLabel: 'github.com/jamemech01/world-market-claude',
        desc: 'NestJS + TypeORM + PostgreSQL marketplace with buyer/seller/delivery roles, JWT auth, RBAC, digital wallet, and interactive store map for location-based ordering.',
      },
      {
        title: 'GPS Vendor',
        url: 'https://github.com/jamemech01/gps-vendor',
        urlLabel: 'github.com/jamemech01/gps-vendor',
        desc: 'Express + EJS + Sequelize + PostgreSQL fleet tracking app with JWT auth, express-validator, and an admin dashboard for real-time vehicle and transport management.',
      },
    ]

    const skills: SkillRow[] = [
      { key: 'Backend',   tags: ['NestJS', 'Express', 'Node.js', 'JWT', 'RBAC'] },
      { key: 'Languages', tags: ['TypeScript', 'JavaScript'] },
      { key: 'Databases', tags: ['PostgreSQL', 'MySQL', 'MongoDB'] },
      { key: 'ORM/ODM',   tags: ['TypeORM', 'Sequelize', 'Mongoose'] },
      { key: 'Tools',     tags: ['Git', 'Docker', 'Postman'] },
    ]

    return { experience, projects, skills }
  },
})
</script>

<style scoped>
:global(body) { margin: 0; }
:global(#app) { margin: 0; padding: 0; }

.rv {
  max-width: 680px;
  margin: 0 auto;
  font-family: 'Inter', sans-serif;
  font-size: 11px;
  color: #1a1a1a;
  line-height: 1.3;
  background: #fff;
  padding: 8px 16px;        /* ลดจาก 10px */
}

@media print {
  .rv { margin: 0; padding: 6px 12px; }
  body { margin: 0; }
}

.name-highlight {
  color: #4b3fa0;
  font-size: 20px;           /* ลดจาก 22px */
  font-weight: 700;
  margin-top: 0;
  margin-bottom: 2px;        /* ลดจาก 3px */
}

.contact-vert {
  display: flex;
  flex-direction: column;
  font-size: 9px;
  gap: 1px;
  margin-bottom: 4px;        /* ลดจาก 5px */
}

.contact-highlight { color: #9d8fe0; }
.contact-vert a { color: inherit; text-decoration: none; }
.contact-vert a:hover { color: #4b3fa0; }

.role {
  font-size: 9px;
  font-style: italic;
  color: #666;
  margin-bottom: 4px;        /* ลดจาก 6px */
  line-height: 1.4;
}

h2 {
  font-size: 8px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1.4px;
  color: #1a1a1a;
  border-bottom: 0.5px solid #d0cce8;
  padding-bottom: 2px;       /* ลดจาก 3px */
  margin-bottom: 6px;        /* ลดจาก 8px */
  margin-top: 8px;           /* ลดจาก 12px */
}

.edu-text {
  font-size: 10.5px;
  color: #1a1a1a;
  margin: 0;
}

.exp-row {
  display: grid;
  grid-template-columns: 1fr 1.6fr;
  gap: 8px;
  margin-bottom: 5px;        /* ลดจาก 7px */
  align-items: start;
}

.exp-left {
  display: flex;
  flex-direction: column;
  gap: 1px;
}

.exp-right {
  border-left: 1.2px solid #d0cce8;
  padding-left: 8px;
  display: flex;
  flex-direction: column;
  gap: 2px;                  /* ลดจาก 3px */
}

.exp-bullet {
  display: flex;
  align-items: flex-start;
  gap: 5px;
}

.bullet-dot {
  width: 4px;
  height: 4px;
  border-radius: 50%;
  background: #9d8fe0;
  margin-top: 4px;
  flex-shrink: 0;
}

.exp-bullet span {
  font-size: 10.5px;
  color: #1a1a1a;
  line-height: 1.3;          /* ลดจาก 1.35 */
}

.entry-title { font-size: 11px; font-weight: 600; }
.entry-meta  { font-size: 10px; color: #555; }
.entry-date  { font-size: 9.5px; color: #888; }

.proj-card { margin-bottom: 5px; }  /* ลดจาก 7px */

.proj-header {
  display: flex;
  align-items: baseline;
  gap: 8px;
  flex-wrap: wrap;
  margin-bottom: 2px;        /* ลดจาก 3px */
}

.proj-url {
  font-size: 9.5px;
  color: #9d8fe0;
  text-decoration: none;
  margin-left: auto;
}
.proj-url:hover { color: #4b3fa0; }

.proj-desc {
  font-size: 10.3px;
  color: #333;
  line-height: 1.35;
  margin: 0;
}

.skills { display: flex; flex-direction: column; gap: 2px; }  /* ลดจาก 3px */

.skill-row {
  display: flex;
  gap: 5px;
  align-items: center;
  flex-wrap: wrap;
}

.skill-key {
  min-width: 64px;
  font-size: 10px;
  color: #555;
  flex-shrink: 0;
}

.skill-tag {
  font-size: 9.5px;
  color: #4b3fa0;
  border: 0.5px solid #c5bee8;
  border-radius: 3px;
  padding: 1px 4px;
  background: #f5f3ff;
}
</style>