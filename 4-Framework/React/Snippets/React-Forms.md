## 📌 Form Library Options

| Library         | Usage      |
| --------------- | ---------- |
| React Hook Form | ⭐⭐⭐⭐⭐ |
| Formik          | ⭐⭐⭐     |
| Native Forms    | ⭐⭐       |

---

## 📌 React Hook Form (RHF)

| Item        | Description                 |
| ----------- | --------------------------- |
| Purpose     | React Form State Management |
| Package     | `react-hook-form`           |
| Type        | Hook-Based                  |
| Performance | Excellent                   |
| Bundle Size | Small                       |

```bash
npm install react-hook-form
```

| Hook / API         | Purpose           |
| ------------------ | ----------------- |
| `useForm()`        | Main Hook         |
| `register()`       | Register Input    |
| `handleSubmit()`   | Handle Submit     |
| `watch()`          | Watch Values      |
| `setValue()`       | Update Field      |
| `getValues()`      | Read Values       |
| `reset()`          | Reset Form        |
| `formState.errors` | Validation Errors |

```jsx
import { useForm } from "react-hook-form";

function Form() {
  const { register, handleSubmit } = useForm();
  const onSubmit = (data) => console.log(data);

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register("name")} />
      <button>Submit</button>
    </form>
  );
}
```

### Common APIs

| API            | Syntax                    |
| -------------- | ------------------------- |
| Register Field | `register("name")`        |
| Submit Form    | `handleSubmit(onSubmit)`  |
| Watch Value    | `watch("name")`           |
| Get Values     | `getValues()`             |
| Set Value      | `setValue("name","John")` |
| Reset Form     | `reset()`                 |

```js
// Most Used APIs
register();
handleSubmit();
watch();
errors;
reset();
setValue();
getValues();
```

### Validation

```jsx
<input
  {...register("email", {
    required: "Email Required",
  })}
/>;

// Error Handling
{
  errors.email && <p>{errors.email.message}</p>;
}
```

| Validation Rules | Example                       |
| ---------------- | ----------------------------- |
| Required         | `{ required: true }`          |
| Min Length       | `{ minLength: 3 }`            |
| Max Length       | `{ maxLength: 20 }`           |
| Pattern          | `{ pattern: /\S+@\S+\.\S+/ }` |
| Custom           | `{ validate: fn }`            |

### useForm()

```js
const {
  register,
  handleSubmit,
  watch,
  reset,
  setValue,
  getValues,
  formState: { errors },
} = useForm();
```

---

## 📌 Formik

| Item        | Description                        |
| ----------- | ---------------------------------- |
| Purpose     | React Form Management Library      |
| Handles     | Form State, Validation, Submission |
| Alternative | React Hook Form                    |
| Common Use  | Login, Signup, Contact Forms       |

```txt
User Input
 ↓
Formik State
 ↓
Validation
 ↓
Submit
 ↓
API Call
```

### Formik vs React Hook Form

| Feature         | Formik         | React Hook Form |
| --------------- | -------------- | --------------- |
| Learning Curve  | Easy           | Easy            |
| Performance     | Good           | Better          |
| Bundle Size     | Larger         | Smaller         |
| Popularity      | High           | Very High       |
| Modern Projects | ⚠️ Less Common | ✅ Preferred    |

```bash
npm install formik
```

```jsx
// Without Formik: Lots of state management.
const [name, setName] = useState("");
const [email, setEmail] = useState("");

// With Formik: Formik manages form state.
<Formik>...</Formik>;
```

| Core Concepts   | Purpose           |
| --------------- | ----------------- |
| `Formik`        | Wrapper Component |
| `useFormik()`   | Hook API          |
| `initialValues` | Default Values    |
| `handleChange`  | Input Updates     |
| `handleSubmit`  | Form Submission   |
| `values`        | Current Form Data |
| `errors`        | Validation Errors |
| `touched`       | Visited Fields    |

### Form State

| Property       | Example            |
| -------------- | ------------------ |
| `values`       | Form Values        |
| `errors`       | Validation Errors  |
| `touched`      | Visited Fields     |
| `isSubmitting` | Loading State      |
| `dirty`        | Form Changed?      |
| `isValid`      | Validation Passed? |

### Validation

```js
validate: (values) => {
  const errors = {};
  if (!values.email) {
    errors.email = "Required";
  }
  return errors;
};
```

### Basic Example

```jsx
import { useFormik } from "formik";

const formik = useFormik({
  initialValues: {
    name: "",
  },

  onSubmit: (values) => {
    console.log(values);
  },
});

<form onSubmit={formik.handleSubmit}>
  <input
    name="name"
    onChange={formik.handleChange}
    value={formik.values.name}
  />

  <button>Submit</button>
</form>;
```

### Formik Props

| Prop              | Purpose        |
| ----------------- | -------------- |
| `values`          | Current Values |
| `errors`          | Error Messages |
| `touched`         | Touched Fields |
| `handleChange`    | Input Change   |
| `handleBlur`      | Blur Event     |
| `handleSubmit`    | Form Submit    |
| `setFieldValue()` | Update Value   |
| `resetForm()`     | Reset Form     |

---

## 📌 Yup Integration

```bash
npm install yup
```

```js
// Schema:
const schema = Yup.object({
  email: Yup.string().required(),
});

// Formik:
validationSchema: schema;
```

---

## 📌 Zod (Most Popular) Integration

```bash
npm install zod
npm install @hookform/resolvers
```

```js
resolver: zodResolver(schema);
```

---
