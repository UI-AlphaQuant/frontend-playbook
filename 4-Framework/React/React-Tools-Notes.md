## 📌 React Hook Form vs Formik

| Feature            | React Hook Form | Formik        |
| ------------------ | --------------- | ------------- |
| Released           | 2019            | 2017          |
| Performance        | ⭐⭐⭐⭐⭐      | ⭐⭐⭐        |
| Re-renders         | Minimal         | More Frequent |
| Bundle Size        | Small           | Larger        |
| Learning Curve     | Medium          | Easy          |
| TypeScript Support | Excellent       | Good          |
| Validation         | Zod, Yup        | Yup           |
| Large Forms        | Excellent       | Good          |
| Popularity (2026)  | ⭐⭐⭐⭐⭐      | ⭐⭐          |
| Industry Adoption  | Modern Apps     | Legacy Apps   |

1. React Hook Form

```tsx
const { register, handleSubmit } = useForm();

<form onSubmit={handleSubmit(onSubmit)}>
  <input {...register("email")} />

  <button>Save</button>
</form>;
```

2. Formik

```tsx
<Formik
  initialValues={{
    email: "",
  }}
  onSubmit={onSubmit}
>
  <Form>
    <Field name="email" />

    <button>Save</button>
  </Form>
</Formik>
```

### Validation

- React Hook Form + Zod (Current Industry Standard)

```ts
z.object({
  email: z.email(),
});
```

- Formik + Yup (Traditional Stack)

```ts
Yup.object({
  email: Yup.string().email(),
});
```

**_React Hook Form:_** Performance-focused form library using uncontrolled components and minimal re-renders.
**_Formik:_** Older form management library using controlled components with higher re-render cost.

---

## 📌 Structure

### public Folder

| Purpose                 | Store Static Assets |
| ----------------------- | ------------------- |
| Location                | `/public`           |
| Processed By Build Tool | ❌ No               |
| Accessible Via URL      | ✅ Yes              |

### Modules

A module is a JavaScript/TypeScript file that exports functionality, allowing code to be organized, reused, and imported across a React application.

| Type             | Example         |
| ---------------- | --------------- |
| Component Module | UserCard.tsx    |
| Hook Module      | useUsers.ts     |
| API Module       | userApi.ts      |
| State Module     | authStore.ts    |
| Context Module   | AuthContext.tsx |
| Utility Module   | formatDate.ts   |
| Type Module      | user.types.ts   |
| Config Module    | env.ts          |

---
