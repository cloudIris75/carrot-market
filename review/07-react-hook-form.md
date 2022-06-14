# 07 React Hook Form

## react-hook-form

### Goals

- [x] Less code
- [x] Better validation
- [x] Better Errors (set, clear, display)
- [x] Have control over inputs
- [x] Don't deal with events
- [x] Easier Inputs

### useForm Hook

1. Connect Input to state
2. Validation
3. Errors

```tsx
// pages/login.tsx
import { useForm } from 'react-hook-form';

interface LoginForm {
  email: string;
  password: string;
}

const Login: NextPage = () => {
  const {
    register,
    handleSubmit,
    formState: { errors },
    watch,
  } = useForm<LoginForm>({ mode: 'onBlur' });
  const onValid = (data: LoginForm) => {
    console.log(watch());
    console.log('success :)!');
  };
  const onInvalid = (errors: FieldErrors) => {
    console.log(errors);
  };
  return (
    <form onSubmit={handleSubmit(onValid, onInvalid)}>
      <Input
        {...register('password', {
          required: '비밀번호는 필수 항목입니다.',
          minLength: {
            message: '비밀번호는 8자 이상이어야 합니다.',
            value: 8,
          },
          validate: {
            notSpecials: (value) =>
              !value.includes('!') || '특수문자는 포함할 수 없습니다.',
          },
        })}
        label="비밀번호"
        type="password"
        classname={`${Boolean(errors.password) ? 'border-red-500' : ''}`}
        required
      />
      <p>{errors.password?.message}</p>
      <Button name="로그인하기" type="submit" />
    </form>
  );
};

export default Login;
```

##### [useForm | React Hook Form - Simple React forms validation](https://react-hook-form.com/api/useform)
