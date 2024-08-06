<script>
    import { invoke } from '@tauri-apps/api/tauri';
  
    let name = '';
    let greetMsg = '';
  
    async function greet() {
        greetMsg = await invoke('greet', { name });
    }
</script>

<style>
    body {
        font-family: 'Arial', sans-serif;
        background-color: #f5f5f5;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
    }

    div {
        background-color: #ffffff;
        border-radius: 12px;
        box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
        padding: 20px;
        width: 100%;
        max-width: 400px;
        text-align: center;
    }

    input {
        width: 100%;
        padding: 12px;
        border: 2px solid #ddd;
        border-radius: 8px;
        font-size: 16px;
        margin-bottom: 16px;
        box-sizing: border-box;
        transition: border-color 0.3s ease;
    }

    input:focus {
        border-color: #007bff;
        outline: none;
    }

    button {
        background-color: #ff0000;
        color: #ffffff;
        border: none;
        padding: 12px 24px;
        border-radius: 8px;
        font-size: 16px;
        cursor: pointer;
        transition: background-color 0.3s ease;
    }

    button:hover {
        background-color: #7ec88c;
    }

    .greetMsg {
        width: fit-content;
        height: fit-content;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #007bff;
        color: #ffffff;
        border: none;
        padding: 12px 24px;
        border-radius: 8px;
        font-size: 16px;
        cursor: pointer;
        transition: opacity 0.3s ease;
        margin: 20px auto; 
        opacity: 0; 
    }

    .greetMsg.show {
        opacity: 1;
    }
</style>

<div>
    <input id="greet-input" placeholder="Enter a name..." bind:value={name} />
    <button on:click={greet}>Greet</button>
    <div class="greetMsg" class:show={greetMsg}>{greetMsg}</div>
</div>
