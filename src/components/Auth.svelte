<script>
  import { supabase } from '../lib/supabase.js'
  import Button from './Button.svelte'
  let email;

  // ログイン処理
  const login = async () => {
    const {error} = await supabase.auth.signIn({email})
    if(error) {
      return console.error(error)
    }
  }
</script>

<h2>ログイン画面</h2>
<input
  type="email"
  placeholder="メールを入力してください。"
  bind:value={email}
>
<Button
  name="ログイン"
  bgColor="bg-blue-500"
  on:click={login}
/>