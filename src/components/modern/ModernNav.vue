<template>
  <nav class="modern-nav" :class="{ 'nav-scrolled': isScrolled }">
    <div class="nav-container">
      <!-- Logo/Brand -->
      <div class="nav-brand">
        <div class="brand-icon">
          <div class="icon-circle"></div>
          <div class="icon-dot"></div>
        </div>
        <span class="brand-text">Portfolio</span>
      </div>
      
      <!-- Desktop Menu -->
      <ul class="nav-menu desktop-menu">
        <li v-for="item in menuItems" :key="item.id" class="nav-item">
          <a 
            :href="item.href" 
            class="nav-link"
            :class="{ 'active': activeSection === item.id }"
            @click="scrollToSection(item.href, item.id)"
          >
            <span class="link-text">{{ item.label }}</span>
            <div class="link-indicator"></div>
          </a>
        </li>
      </ul>
      
      <!-- Theme Toggle -->
      <button class="theme-toggle" @click="toggleTheme">
        <div class="toggle-track">
          <div class="toggle-thumb" :class="{ 'dark': isDark }">
            <span class="toggle-icon">{{ isDark ? '🌙' : '☀️' }}</span>
          </div>
        </div>
      </button>
      
      <!-- Mobile Menu Button -->
      <button class="mobile-menu-btn" @click="toggleMobileMenu">
        <span class="hamburger" :class="{ 'open': isMobileOpen }"></span>
      </button>
    </div>
    
    <!-- Mobile Menu -->
    <div class="mobile-menu" :class="{ 'open': isMobileOpen }">
      <ul class="mobile-nav-list">
        <li v-for="item in menuItems" :key="item.id" class="mobile-nav-item">
          <a 
            :href="item.href" 
            class="mobile-nav-link"
            @click="scrollToSection(item.href, item.id); closeMobileMenu()"
          >
            {{ item.label }}
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'ModernNav',
  data() {
    return {
      isScrolled: false,
      activeSection: 'hero',
      isDark: false,
      isMobileOpen: false,
      menuItems: [
        { id: 'hero', label: '首页', href: '#hero' },
        { id: 'about', label: '关于', href: '#about' },
        { id: 'experience', label: '经历', href: '#experience' },
        { id: 'skills', label: '技能', href: '#skills' },
        { id: 'projects', label: '项目', href: '#projects' },
        { id: 'contact', label: '联系', href: '#contact' }
      ]
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
    this.observeSections();
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 50;
    },
    toggleTheme() {
      this.isDark = !this.isDark;
      document.documentElement.classList.toggle('dark', this.isDark);
    },
    toggleMobileMenu() {
      this.isMobileOpen = !this.isMobileOpen;
    },
    closeMobileMenu() {
      this.isMobileOpen = false;
    },
    scrollToSection(href, id) {
      this.activeSection = id;
      if (href.startsWith('#')) {
        const element = document.querySelector(href);
        if (element) {
          element.scrollIntoView({ 
            behavior: 'smooth',
            block: 'start'
          });
        }
      }
    },
    observeSections() {
      const sections = document.querySelectorAll('section[id]');
      const observer = new IntersectionObserver(
        (entries) => {
          entries.forEach(entry => {
            if (entry.isIntersecting) {
              this.activeSection = entry.target.id;
            }
          });
        },
        { threshold: 0.3 }
      );
      
      sections.forEach(section => observer.observe(section));
    }
  }
}
</script>

<style scoped>
.modern-nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.2);
  transition: var(--transition-all);
}

.nav-scrolled {
  background: rgba(255, 255, 255, 0.95);
  box-shadow: var(--shadow-lg);
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--space-6);
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 80px;
}

.nav-brand {
  display: flex;
  align-items: center;
  gap: var(--space-3);
  font-weight: var(--font-bold);
  font-size: var(--text-xl);
  color: var(--gray-800);
}

.brand-icon {
  position: relative;
  width: 32px;
  height: 32px;
}

.icon-circle {
  width: 100%;
  height: 100%;
  background: var(--gradient-primary);
  border-radius: 50%;
  animation: float 3s ease-in-out infinite;
}

.icon-dot {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 8px;
  height: 8px;
  background: white;
  border-radius: 50%;
}

.desktop-menu {
  display: flex;
  align-items: center;
  gap: var(--space-8);
  list-style: none;
}

.nav-link {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--space-1);
  padding: var(--space-2) 0;
  color: var(--gray-600);
  text-decoration: none;
  font-weight: var(--font-medium);
  transition: var(--transition-colors);
}

.nav-link:hover,
.nav-link.active {
  color: var(--primary);
}

.link-indicator {
  width: 0;
  height: 2px;
  background: var(--gradient-primary);
  border-radius: var(--radius-full);
  transition: var(--transition-all);
}

.nav-link:hover .link-indicator,
.nav-link.active .link-indicator {
  width: 100%;
}

.theme-toggle {
  background: none;
  border: none;
  cursor: pointer;
  padding: var(--space-2);
}

.toggle-track {
  width: 50px;
  height: 26px;
  background: var(--gray-200);
  border-radius: var(--radius-full);
  position: relative;
  transition: var(--transition-all);
}

.toggle-thumb {
  position: absolute;
  top: 2px;
  left: 2px;
  width: 22px;
  height: 22px;
  background: white;
  border-radius: 50%;
  transition: var(--transition-all);
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: var(--shadow);
}

.toggle-thumb.dark {
  transform: translateX(24px);
  background: var(--gray-800);
}

.toggle-thumb.dark ~ .toggle-track {
  background: var(--primary);
}

.toggle-icon {
  font-size: 12px;
}

.mobile-menu-btn {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: var(--space-2);
}

.hamburger {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--gray-800);
  position: relative;
  transition: var(--transition-all);
}

.hamburger::before,
.hamburger::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 2px;
  background: var(--gray-800);
  transition: var(--transition-all);
}

.hamburger::before {
  top: -8px;
}

.hamburger::after {
  bottom: -8px;
}

.hamburger.open {
  background: transparent;
}

.hamburger.open::before {
  transform: rotate(45deg);
  top: 0;
}

.hamburger.open::after {
  transform: rotate(-45deg);
  bottom: 0;
}

.mobile-menu {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.2);
  transform: translateY(-100%);
  opacity: 0;
  visibility: hidden;
  transition: var(--transition-all);
}

.mobile-menu.open {
  transform: translateY(0);
  opacity: 1;
  visibility: visible;
}

.mobile-nav-list {
  list-style: none;
  padding: var(--space-6);
}

.mobile-nav-item {
  margin-bottom: var(--space-4);
}

.mobile-nav-link {
  display: block;
  padding: var(--space-3);
  color: var(--gray-800);
  text-decoration: none;
  font-weight: var(--font-medium);
  border-radius: var(--radius-lg);
  transition: var(--transition-all);
}

.mobile-nav-link:hover {
  background: var(--gray-100);
  color: var(--primary);
}

@media (max-width: 768px) {
  .desktop-menu,
  .theme-toggle {
    display: none;
  }
  
  .mobile-menu-btn {
    display: block;
  }
  
  .nav-container {
    padding: 0 var(--space-4);
    height: 70px;
  }
}
</style>
