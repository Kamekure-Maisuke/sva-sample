<script>
  import { memos,addMemos,deleteMemos } from '../stores/memoStore.js'
  import Button from '../components/Button.svelte'
  import { loadMemos } from '../stores/memoStore.js'

  // メモ履歴
  loadMemos()
  // テキストエリア入力欄
  let newMemo = '';
  // 登録ボタン押下時の処理
  const registerClick = () => {
    addMemos(newMemo)
    newMemo = ''
  }
</script>

<textarea
  class="
    form-control
    block
    w-full
    px-3
    py-1.5
    text-base
    font-normal
    text-gray-700
    bg-white bg-clip-padding
    border border-solid border-gray-300
    rounded
    transition
    ease-in-out
    m-0
    focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none
  "
  rows="3"
  placeholder="メモを入力してください。"
  bind:value={newMemo}
></textarea>
<Button
  name="登録"
  bgColor="bg-blue-400"
  on:click={registerClick}
/>

{#each $memos as memo}
  <li>
    {memo.body}
    <Button
      name="削除"
      bgColor="bg-red-400"
      on:click={() => deleteMemos(memo.id)}
    />
  </li>
{/each}