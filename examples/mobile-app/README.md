# Mobile App Example

> HiveLoop configuration for React Native / Expo apps

---

## Project Structure

```
my-mobile-app/
├── .hiveloop/
│   ├── prd.md
│   ├── tech_stack.md
│   ├── conventions.md
│   ├── implementation_plan.md
│   └── progress_tracker.md
├── app/
│   ├── src/
│   │   ├── screens/
│   │   ├── components/
│   │   └── stores/
│   └── app.json
└── api/
    └── src/
```

---

## Tech Stack Example

```markdown
## Mobile
- Expo SDK 51
- React Native 0.74
- TypeScript 5.0
- NativeWind 4.0

## State
- Zustand 4.5

## Navigation
- React Navigation 6.x

## Backend
- FastAPI
- PostgreSQL
```

---

## Agent Assignment

| Domain | Agent | Tasks |
|--------|-------|-------|
| Screens | Frontend | UI implementation |
| Components | Frontend | Reusable elements |
| State | Frontend | Zustand stores |
| API Endpoints | Backend | FastAPI routes |
| Device Features | BLE Agent | Native modules |

---

## Mobile-Specific Considerations

### BLE Agent
For Bluetooth/device connectivity:
- Requires native builds (not Expo Go)
- Test on physical devices only
- Handle permission flows

### Navigation
```typescript
// Screen registration pattern
const Stack = createNativeStackNavigator();

function App() {
  return (
    <Stack.Navigator>
      <Stack.Screen name="Home" component={HomeScreen} />
    </Stack.Navigator>
  );
}
```

---

## Sample Iteration

```markdown
## Iteration 3 - Mobile App

### Orchestrator
Ready: HomeScreen, SettingsScreen, API endpoints

### Spawned
| Agent | Tasks |
|-------|-------|
| Frontend | HomeScreen, SettingsScreen |
| Backend | /home/status, /settings |

### Results
- Completed: 4/4
- Patterns: NativeWind responsive pattern
```

---

## Key Patterns

### Screen Pattern
```typescript
export function HomeScreen() {
  const { status } = useHomeStore();
  
  return (
    <View className="flex-1 bg-white">
      <StatusCard status={status} />
    </View>
  );
}
```

### Store Pattern
```typescript
const useHomeStore = create<HomeState>((set) => ({
  status: null,
  fetchStatus: async () => {
    const data = await api.get('/home/status');
    set({ status: data });
  },
}));
```
