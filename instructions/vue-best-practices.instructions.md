---
applyTo: "**/*.{vue,js,ts}"
---

# Vue.js Best Practices and Standards

**Purpose** – Enforce consistent Vue.js 3 development patterns, Composition API usage, and modern best practices.

**Guidelines:**
- Use Composition API with `<script setup>` syntax
- Prefer TypeScript for type safety and better DX
- Use single-file components (.vue) structure
- Follow Vue.js official style guide conventions
- Implement proper reactivity patterns with ref/reactive
- Use proper component naming (multi-word, PascalCase)
- Apply scoped styling or CSS modules
- Implement proper prop validation and emit definitions
- Use proper lifecycle hooks and composables
- Follow performance optimization patterns

**When to Apply:**
1. Component creation and structure
2. State management implementation
3. Props and events handling
4. Template and styling
5. Performance optimization
6. Testing and deployment

**Project Structure:**
```
src/
├── components/
│   ├── ui/                 # Reusable UI components
│   ├── forms/              # Form components
│   └── layout/             # Layout components
├── composables/            # Reusable composition functions
├── views/                  # Route components
├── stores/                 # Pinia stores
├── router/                 # Vue Router configuration
├── plugins/                # Vue plugins
├── utils/                  # Utility functions
├── types/                  # TypeScript definitions
└── assets/                 # Static assets
```

**Key Patterns:**

**Component Structure:**
```vue
<template>
  <div class="user-profile">
    <h1>{{ user.name }}</h1>
    <button @click="handleUpdate" :disabled="isLoading">
      Update Profile
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'
import { useUserStore } from '@/stores/user'

interface Props {
  userId: string
  editable?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  editable: false
})

const emit = defineEmits<{
  update: [user: User]
  error: [message: string]
}>()

const userStore = useUserStore()
const isLoading = ref(false)

const user = computed(() => userStore.getUserById(props.userId))

const handleUpdate = async () => {
  isLoading.value = true
  try {
    await userStore.updateUser(props.userId)
    emit('update', user.value)
  } catch (error) {
    emit('error', error.message)
  } finally {
    isLoading.value = false
  }
}

onMounted(() => {
  userStore.fetchUser(props.userId)
})
</script>

<style scoped>
.user-profile {
  padding: 1rem;
}
</style>
```

**Composable:**
```typescript
// composables/useApi.ts
import { ref, Ref } from 'vue'

export function useApi<T>(url: string) {
  const data: Ref<T | null> = ref(null)
  const loading = ref(false)
  const error = ref<string | null>(null)

  const execute = async () => {
    loading.value = true
    error.value = null
    
    try {
      const response = await fetch(url)
      if (!response.ok) throw new Error('Failed to fetch')
      data.value = await response.json()
    } catch (err) {
      error.value = err.message
    } finally {
      loading.value = false
    }
  }

  return {
    data: readonly(data),
    loading: readonly(loading),
    error: readonly(error),
    execute
  }
}
```

**Store (Pinia):**
```typescript
// stores/user.ts
import { defineStore } from 'pinia'
import { ref, computed } from 'vue'

export const useUserStore = defineStore('user', () => {
  const users = ref<User[]>([])
  const currentUser = ref<User | null>(null)

  const getUserById = computed(() => (id: string) => 
    users.value.find(user => user.id === id)
  )

  const fetchUser = async (id: string) => {
    const response = await fetch(`/api/users/${id}`)
    const user = await response.json()
    currentUser.value = user
  }

  const updateUser = async (id: string, data: Partial<User>) => {
    const response = await fetch(`/api/users/${id}`, {
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(data)
    })
    
    if (!response.ok) throw new Error('Update failed')
    
    const updatedUser = await response.json()
    const index = users.value.findIndex(u => u.id === id)
    if (index !== -1) users.value[index] = updatedUser
  }

  return {
    users,
    currentUser,
    getUserById,
    fetchUser,
    updateUser
  }
})
```

**Component Best Practices:**
- Use multi-word component names (e.g., `UserProfile`, `BlogPost`)
- Always use `key` with `v-for` for component state consistency
- Avoid `v-if` with `v-for` on the same element
- Use detailed prop definitions with TypeScript
- Implement proper event handling with `defineEmits`
- Use scoped styles or CSS modules for styling

**Reactivity Patterns:**
- Use `ref()` for primitive values and `reactive()` for objects
- Prefer `computed()` for derived state
- Use `watch()` for side effects, `watchEffect()` for reactive dependencies
- Implement proper cleanup in `onUnmounted`
- Use `shallowRef()` for large immutable structures

**Performance Optimization:**
- Use `v-once` for static content that never changes
- Implement `v-memo` for expensive list rendering
- Use `defineAsyncComponent` for code splitting
- Implement virtual scrolling for large lists
- Use `shallowRef`/`shallowReactive` for large datasets
- Avoid unnecessary component abstractions

**Template Best Practices:**
- Use semantic HTML elements
- Implement proper event handling
- Use proper attribute binding (`:` vs `v-bind`)
- Apply consistent naming conventions
- Use template refs sparingly and with proper typing

**TypeScript Integration:**
- Use `<script setup lang="ts">` syntax
- Define proper interfaces for props and emits
- Use generic types for reusable components
- Implement proper type guards and assertions
- Use `PropType` for complex prop types when needed

**Testing:**
- Write unit tests for components and composables
- Use Vue Test Utils for component testing
- Test user interactions and state changes
- Mock external dependencies
- Test accessibility features

**Security:**
- Sanitize user inputs in templates
- Use `v-html` with caution
- Validate props and emit payloads
- Implement proper CORS policies
- Use HTTPS in production

**Output Format:**
- Follow Vue.js style guide conventions
- Use TypeScript for type safety
- Implement proper component hierarchy
- Apply consistent naming patterns
- Use proper code organization
- Include proper documentation
