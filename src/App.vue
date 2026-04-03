<script setup>
import { ref } from 'vue'

const navLinks = [
  { label: 'Hero', href: '#hero' },
  { label: 'Ecosystem', href: '#ecosystem' },
  { label: 'Builds', href: '#builds' },
  { label: 'Experience', href: '#experience' },
  { label: 'Contact', href: '#contact' },
]

const activeSection = ref('hero')
const isMenuOpen = ref(false)

const handleNavClick = (href) => {
  activeSection.value = href.replace('#', '')
  isMenuOpen.value = false
}

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}
</script>

<template>
  <div class="min-h-screen bg-background text-on-background font-body">
    <nav class="fixed top-0 w-full z-50 bg-surface/40 backdrop-blur-xl shadow-glow-cyan">
      <div class="flex justify-between items-center px-8 py-4 max-w-screen-xl mx-auto">
        <div class="text-2xl font-bold tracking-tighter text-primary font-headline">KINETIC_ENG</div>

        <div class="hidden md:flex gap-8 items-center">
          <a
            v-for="link in navLinks"
            :key="link.href"
            :href="link.href"
            :class="[
              'font-headline tracking-tighter transition-colors',
              activeSection === link.href.replace('#', '')
                ? 'text-primary font-bold border-b-2 border-primary pb-1'
                : 'text-on-surface-variant font-medium hover:text-primary/80'
            ]"
            @click="handleNavClick(link.href)"
          >
            {{ link.label }}
          </a>
        </div>

        <div class="hidden md:flex gap-4">
          <span class="material-symbols-outlined text-primary cursor-pointer hover:scale-110 transition-transform">terminal</span>
          <span class="material-symbols-outlined text-primary cursor-pointer hover:scale-110 transition-transform">code</span>
        </div>

        <button 
          class="md:hidden flex flex-col gap-1.5 p-2 cursor-pointer"
          @click="toggleMenu"
          aria-label="Toggle menu"
        >
          <span 
            :class="[
              'w-6 h-0.5 bg-primary transition-all duration-300',
              isMenuOpen && 'rotate-45'
            ]"
            :style="isMenuOpen ? 'transform: translateY(8px)' : ''"
          ></span>
          <span 
            :class="[
              'w-6 h-0.5 bg-primary transition-all duration-300',
              isMenuOpen && 'opacity-0'
            ]"
          ></span>
          <span 
            :class="[
              'w-6 h-0.5 bg-primary transition-all duration-300',
              isMenuOpen && 'rotate-[-45deg]'
            ]"
            :style="isMenuOpen ? 'transform: translateY(-8px)' : ''"
          ></span>
        </button>
      </div>

      <div 
        :class="[
          'md:hidden overflow-hidden transition-all duration-300 ease-in-out',
          isMenuOpen ? 'max-h-96 opacity-100' : 'max-h-0 opacity-0'
        ]"
      >
        <div class="px-8 py-4 bg-surface-container border-t border-outline-variant/10">
          <div class="flex flex-col gap-4">
            <a
              v-for="link in navLinks"
              :key="link.href"
              :href="link.href"
              :class="[
                'font-headline tracking-tighter transition-colors py-2',
                activeSection === link.href.replace('#', '')
                  ? 'text-primary font-bold'
                  : 'text-on-surface-variant font-medium hover:text-primary/80'
              ]"
              @click="handleNavClick(link.href)"
            >
              {{ link.label }}
            </a>
          </div>
          <div class="flex gap-4 mt-4 pt-4 border-t border-outline-variant/10">
            <span class="material-symbols-outlined text-primary cursor-pointer hover:scale-110 transition-transform">terminal</span>
            <span class="material-symbols-outlined text-primary cursor-pointer hover:scale-110 transition-transform">code</span>
          </div>
        </div>
      </div>
    </nav>

    <main>
      <section id="hero" class="relative min-h-screen flex items-center pt-20 px-8 overflow-hidden bg-surface">
        <div class="absolute inset-0 z-0 opacity-20 pointer-events-none">
          <div class="absolute top-1/4 -left-20 w-96 h-96 bg-primary rounded-full blur-[128px]"></div>
          <div class="absolute bottom-1/4 -right-20 w-96 h-96 bg-secondary rounded-full blur-[128px]"></div>
        </div>

        <div class="max-w-screen-xl mx-auto w-full grid md:grid-cols-12 gap-12 items-center relative z-10">
          <div class="md:col-span-8">
            <div class="mb-6 inline-flex items-center gap-2 px-3 py-1 rounded-full bg-surface-container-highest/50 backdrop-blur-md">
              <span class="w-2 h-2 rounded-full bg-primary animate-pulse"></span>
              <span class="text-[10px] uppercase tracking-[0.2em] font-bold text-primary-fixed">Engineered for Evolution</span>
            </div>

            <h1 class="font-headline text-5xl md:text-8xl font-bold tracking-tighter leading-[0.9] text-on-background mb-8">
              Building <span class="text-transparent bg-clip-text bg-gradient-to-br from-primary to-secondary">Algorithmic</span> Evolution
            </h1>

            <p class="font-body text-lg md:text-xl text-on-surface-variant max-w-2xl mb-12 leading-relaxed">
              Full Stack Developer forging scalable architectures. Current student at 
              <span class="text-on-surface font-semibold">Universidad Politécnica de Aguascalientes</span>, 
              merging computational theory with high-performance production builds.
            </p>

            <div class="flex flex-wrap gap-6">
              <a class="px-8 py-4 bg-gradient-to-br from-primary-container to-secondary-container text-on-primary-fixed font-bold rounded-lg hover:scale-95 transition-transform flex items-center gap-3" href="#builds">
                Explore Repository
                <span class="material-symbols-outlined">arrow_forward</span>
              </a>
              <a class="px-8 py-4 bg-surface-bright/10 backdrop-blur-xl border border-outline-variant/20 text-on-background font-bold rounded-lg hover:bg-surface-bright/20 transition-all" href="#contact">
                Contact Architect
              </a>
            </div>
          </div>

          <div class="md:col-span-4 hidden md:block">
            <div class="relative w-full aspect-square bg-surface-container rounded-xl overflow-hidden shadow-2xl">
              <div class="absolute inset-0 bg-gradient-to-t from-background to-transparent opacity-60"></div>
              <img 
                class="w-full h-full object-cover grayscale brightness-75 contrast-125" 
                alt="Abstract 3D rendered geometric structures"
                src="https://lh3.googleusercontent.com/aida-public/AB6AXuAGn0XwIgrb23KOH_YIS7u76Y-ToXn8Raxt8-Ns57hOVIFQM2XYAo-Kc7MJRUjkqPSVNQeteLhzkIqAdhpKPXPYWJu2P7we1YnHGiLzMzx17Mb7ItJk2hoTw81_E4oBEWOoiIQ-e5JeQyig8EL6HwJFtU7oBUOhZZbRxPlKbDEsdZh8wkkRcVU8He2ya1YMCIvtew5LpAjSRdMoBNqB0z1CB_yjC7fgkFncb8Ezuy_51xRoljsPBmrPgfpYXYCD8kdBi5PU_lbgIG0"
              />
              <div class="absolute bottom-6 left-6 right-6">
                <div class="glass-card p-4 rounded-lg border border-outline-variant/10">
                  <div class="flex justify-between items-end">
                    <div>
                      <p class="text-[10px] text-primary tracking-widest uppercase mb-1">Current Node</p>
                      <p class="font-headline font-bold text-xl">UPA_SYSTEM_01</p>
                    </div>
                    <span class="material-symbols-outlined text-4xl text-primary/40">sensors</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="ecosystem" class="py-32 px-8 bg-surface-container-low">
        <div class="max-w-screen-xl mx-auto">
          <div class="grid md:grid-cols-2 gap-16 items-start mb-24">
            <h2 class="font-headline text-4xl md:text-6xl font-bold tracking-tighter text-on-background">
              The Tech <br/> <span class="text-secondary">Ecosystem</span>
            </h2>
            <p class="text-on-surface-variant text-lg leading-relaxed pt-2">
              A curated selection of high-level abstractions and foundational languages used to construct resilient, evolutionary software. No bloated dependencies, just pure technical efficiency.
            </p>
          </div>

          <div class="grid grid-cols-2 md:grid-cols-5 gap-px bg-outline-variant/10 rounded-xl overflow-hidden">
            <div class="bg-surface group p-12 flex flex-col items-center justify-center gap-6 hover:bg-surface-container transition-all duration-500 cursor-pointer">
              <div class="w-16 h-16 rounded-full bg-surface-container-high flex items-center justify-center group-hover:scale-110 transition-transform">
                <span class="material-symbols-outlined text-4xl text-primary">layers</span>
              </div>
              <span class="font-headline font-bold text-xl tracking-tight">Vue.js</span>
            </div>

            <div class="bg-surface group p-12 flex flex-col items-center justify-center gap-6 hover:bg-surface-container transition-all duration-500 cursor-pointer">
              <div class="w-16 h-16 rounded-full bg-surface-container-high flex items-center justify-center group-hover:scale-110 transition-transform">
                <span class="material-symbols-outlined text-4xl text-secondary">animation</span>
              </div>
              <span class="font-headline font-bold text-xl tracking-tight">React</span>
            </div>

            <div class="bg-surface group p-12 flex flex-col items-center justify-center gap-6 hover:bg-surface-container transition-all duration-500 cursor-pointer">
              <div class="w-16 h-16 rounded-full bg-surface-container-high flex items-center justify-center group-hover:scale-110 transition-transform">
                <span class="material-symbols-outlined text-4xl text-primary">verified</span>
              </div>
              <span class="font-headline font-bold text-xl tracking-tight">TypeScript</span>
            </div>

            <div class="bg-surface group p-12 flex flex-col items-center justify-center gap-6 hover:bg-surface-container transition-all duration-500 cursor-pointer">
              <div class="w-16 h-16 rounded-full bg-surface-container-high flex items-center justify-center group-hover:scale-110 transition-transform">
                <span class="material-symbols-outlined text-4xl text-secondary">database</span>
              </div>
              <span class="font-headline font-bold text-xl tracking-tight">Laravel</span>
            </div>

            <div class="bg-surface group p-12 flex flex-col items-center justify-center gap-6 hover:bg-surface-container transition-all duration-500 cursor-pointer">
              <div class="w-16 h-16 rounded-full bg-surface-container-high flex items-center justify-center group-hover:scale-110 transition-transform">
                <span class="material-symbols-outlined text-4xl text-primary">memory</span>
              </div>
              <span class="font-headline font-bold text-xl tracking-tight">Python</span>
            </div>
          </div>
        </div>
      </section>

      <section id="builds" class="py-32 px-8 bg-surface">
        <div class="max-w-screen-xl mx-auto">
          <div class="mb-16">
            <p class="text-primary font-bold tracking-[0.3em] uppercase text-xs mb-4">Case Study // 001</p>
            <h2 class="font-headline text-4xl md:text-6xl font-bold tracking-tighter text-on-background">Featured Build</h2>
          </div>

          <div class="grid md:grid-cols-2 gap-0 bg-surface-container rounded-2xl overflow-hidden shadow-2xl relative border border-outline-variant/10">
            <div class="relative h-96 md:h-full">
              <img 
                class="w-full h-full object-cover" 
                alt="Bio-Logix dashboard showing genetic algorithm data visualizations"
                src="https://lh3.googleusercontent.com/aida-public/AB6AXuCHBiBfCXI0hSTvnZ-rO1lBy0yFDTjxNaHgffyWpV_aGdINH8NisgIbO9XQE0ZB919mjejd6PiLl_4mP_xYCKsyREwiPgpblfE_xYSJ_tvlWt-aGhxYuIEelDsHhcedaMWOLbx_NS8ngxyOjbAFn5rwxzYl9rn-Svzx1_HdR5mbLQVeQWApF3WxP0DdOVF5BT1hR5bLF65pgixrfsQyMc7AcSJqEZ2B8v__aG2-GB5yw3qNRhjQb3-a-pNDRVISNx9UkZnlhdRSt0I"
              />
              <div class="absolute inset-0 bg-gradient-to-r from-surface-container via-transparent to-transparent hidden md:block"></div>
            </div>

            <div class="p-12 flex flex-col justify-center">
              <h3 class="font-headline text-5xl font-bold mb-6 tracking-tighter">Bio-Logix</h3>
              <p class="text-on-surface-variant text-lg leading-relaxed mb-8">
                A high-performance Genetic Algorithm Simulator designed to visualize evolutionary trajectories in real-time. Built to process multi-variable populations with optimized compute cycles.
              </p>

              <div class="grid grid-cols-2 gap-8 mb-12">
                <div>
                  <p class="text-[10px] text-on-surface-variant tracking-[0.2em] uppercase mb-1">Performance</p>
                  <p class="text-2xl font-bold font-headline text-primary">0.02ms <span class="text-sm font-normal text-on-surface-variant">/gen</span></p>
                </div>
                <div>
                  <p class="text-[10px] text-on-surface-variant tracking-[0.2em] uppercase mb-1">Population</p>
                  <p class="text-2xl font-bold font-headline text-secondary">10k+ <span class="text-sm font-normal text-on-surface-variant">entities</span></p>
                </div>
              </div>

              <div class="flex flex-wrap gap-4 mb-12">
                <span class="px-3 py-1 bg-surface-container-highest rounded text-xs font-medium text-on-surface flex items-center gap-2">
                  <span class="w-1 h-1 rounded-full bg-primary"></span> React Three Fiber
                </span>
                <span class="px-3 py-1 bg-surface-container-highest rounded text-xs font-medium text-on-surface flex items-center gap-2">
                  <span class="w-1 h-1 rounded-full bg-primary"></span> Web Workers
                </span>
              </div>

              <button class="w-fit glass-card px-10 py-4 text-on-background font-bold rounded-lg border border-primary/20 hover:bg-primary/10 transition-all flex items-center gap-3">
                Ver Demo
                <span class="material-symbols-outlined text-primary">rocket_launch</span>
              </button>
            </div>
          </div>
        </div>
      </section>

      <section id="experience" class="py-32 px-8 bg-surface-container-low">
        <div class="max-w-screen-xl mx-auto">
          <div class="flex flex-col md:flex-row justify-between items-end gap-8 mb-24">
            <div class="max-w-2xl">
              <h2 class="font-headline text-4xl md:text-6xl font-bold tracking-tighter text-on-background mb-6">Experience <span class="text-primary">&</span> Narrative</h2>
              <p class="text-on-surface-variant text-lg leading-relaxed">Bridging the gap between academic excellence and commercial implementation through strategic freelance and research-driven initiatives.</p>
            </div>
            <div class="text-right hidden md:block">
              <p class="text-primary font-bold font-headline text-5xl">2024</p>
              <p class="text-on-surface-variant tracking-widest uppercase text-xs">Architectural Year</p>
            </div>
          </div>

          <div class="space-y-12">
            <div class="group relative bg-surface-container p-12 rounded-xl transition-all duration-500 hover:bg-surface-container-high border-l-4 border-primary cursor-pointer">
              <div class="flex flex-col md:flex-row justify-between md:items-center gap-6">
                <div>
                  <h4 class="text-2xl font-bold font-headline mb-2">Freelance Full Stack Developer</h4>
                  <p class="text-primary font-medium">Hotel Real del Gorrión</p>
                </div>
                <div class="px-4 py-2 bg-surface-container-highest rounded text-sm font-mono text-on-surface-variant">
                  JAN 2023 — PRESENT
                </div>
              </div>
              <p class="mt-8 text-on-surface-variant leading-relaxed max-w-4xl">
                Architected an end-to-end reservation system and administrative dashboard. Implemented real-time booking updates and secure payment gateway integrations, reducing administrative overhead by 40%.
              </p>
            </div>

            <div class="group relative bg-surface-container p-12 rounded-xl transition-all duration-500 hover:bg-surface-container-high border-l-4 border-secondary cursor-pointer">
              <div class="flex flex-col md:flex-row justify-between md:items-center gap-6">
                <div>
                  <h4 class="text-2xl font-bold font-headline mb-2">Lead Academic Researcher</h4>
                  <p class="text-secondary font-medium">Universidad Politécnica de Aguascalientes</p>
                </div>
                <div class="px-4 py-2 bg-surface-container-highest rounded text-sm font-mono text-on-surface-variant">
                  AUG 2022 — DEC 2023
                </div>
              </div>
              <p class="mt-8 text-on-surface-variant leading-relaxed max-w-4xl">
                Developed internal tools for complex data analysis across engineering departments. Specialized in visualizing multifaceted datasets to assist in faculty research projects.
              </p>
            </div>
          </div>
        </div>
      </section>

      <section id="contact" class="py-32 px-8 bg-surface">
        <div class="max-w-screen-xl mx-auto grid md:grid-cols-2 gap-24 items-start">
          <div>
            <h2 class="font-headline text-5xl md:text-7xl font-bold tracking-tighter text-on-background mb-8">Initiate <br/> Connection</h2>
            <p class="text-on-surface-variant text-xl leading-relaxed mb-12 max-w-md">
              Ready to discuss systems architecture, full stack development, or algorithmic evolution. Use the terminal below to reach out.
            </p>

            <div class="space-y-6">
              <div class="flex items-center gap-6 group cursor-pointer">
                <div class="w-14 h-14 rounded-lg bg-surface-container-high flex items-center justify-center text-primary group-hover:bg-primary group-hover:text-on-primary-fixed transition-all">
                  <span class="material-symbols-outlined">alternate_email</span>
                </div>
                <div>
                  <p class="text-xs text-on-surface-variant uppercase tracking-widest">Email</p>
                  <p class="text-lg font-bold font-headline">kinetic.eng@dev.io</p>
                </div>
              </div>

              <div class="flex items-center gap-6 group cursor-pointer">
                <div class="w-14 h-14 rounded-lg bg-surface-container-high flex items-center justify-center text-secondary group-hover:bg-secondary group-hover:text-on-secondary transition-all">
                  <span class="material-symbols-outlined">terminal</span>
                </div>
                <div>
                  <p class="text-xs text-on-surface-variant uppercase tracking-widest">Network</p>
                  <p class="text-lg font-bold font-headline">Aguascalientes, MX</p>
                </div>
              </div>
            </div>
          </div>

          <div class="bg-surface-container-low p-10 rounded-2xl border border-outline-variant/10 shadow-2xl relative">
            <div class="absolute top-4 right-6 flex gap-2">
              <div class="w-2 h-2 rounded-full bg-error/40"></div>
              <div class="w-2 h-2 rounded-full bg-primary/40"></div>
              <div class="w-2 h-2 rounded-full bg-secondary/40"></div>
            </div>

            <form action="#" class="space-y-8 mt-4">
              <div class="grid grid-cols-2 gap-8">
                <div class="space-y-2">
                  <label class="text-[10px] uppercase tracking-widest text-on-surface-variant font-bold">Identifier</label>
                  <input 
                    class="w-full bg-surface-container-lowest border-none rounded-lg focus:ring-1 focus:ring-primary text-on-surface p-4 transition-all" 
                    placeholder="Your Name" 
                    type="text"
                  />
                </div>
                <div class="space-y-2">
                  <label class="text-[10px] uppercase tracking-widest text-on-surface-variant font-bold">Endpoint</label>
                  <input 
                    class="w-full bg-surface-container-lowest border-none rounded-lg focus:ring-1 focus:ring-primary text-on-surface p-4 transition-all" 
                    placeholder="Email Address" 
                    type="email"
                  />
                </div>
              </div>

              <div class="space-y-2">
                <label class="text-[10px] uppercase tracking-widest text-on-surface-variant font-bold">Transmission</label>
                <textarea 
                  class="w-full bg-surface-container-lowest border-none rounded-lg focus:ring-1 focus:ring-primary text-on-surface p-4 transition-all" 
                  placeholder="Brief your project or inquiry..." 
                  rows="4"
                ></textarea>
              </div>

              <button 
                class="w-full py-4 bg-primary text-on-primary-fixed font-black uppercase tracking-[0.2em] rounded-lg hover:brightness-110 active:scale-[0.98] transition-all" 
                type="submit"
              >
                Deploy Message
              </button>
            </form>
          </div>
        </div>
      </section>
    </main>

    <footer class="w-full py-12 border-t border-cyan-900/10 bg-surface-dim">
      <div class="flex flex-col md:flex-row justify-between items-center px-8 max-w-screen-xl mx-auto gap-8">
        <div class="text-primary font-black text-xl tracking-tighter">KINETIC_ENG</div>

        <div class="flex gap-8">
          <a class="font-label text-xs uppercase tracking-widest text-on-surface-variant hover:text-primary transition-colors opacity-80 hover:opacity-100" href="#">GitHub</a>
          <a class="font-label text-xs uppercase tracking-widest text-on-surface-variant hover:text-primary transition-colors opacity-80 hover:opacity-100" href="#">LinkedIn</a>
          <a class="font-label text-xs uppercase tracking-widest text-on-surface-variant hover:text-primary transition-colors opacity-80 hover:opacity-100" href="#">Source</a>
          <a class="font-label text-xs uppercase tracking-widest text-on-surface-variant hover:text-primary transition-colors opacity-80 hover:opacity-100" href="#">Status</a>
        </div>

        <p class="font-label text-xs uppercase tracking-widest text-on-surface-variant">
          © 2024 KINETIC_ENG // ALGORITHMIC_ARCHITECT
        </p>
      </div>
    </footer>
  </div>
</template>
