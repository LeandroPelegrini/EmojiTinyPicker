<script>
    import Picker from 'emoji-picker-element/svelte'

    const picker = new Picker();
    picker.dataSource = './assets/emojilist.js';
    let pickemojis = [];
    let pickemoji = '';
    let i = -1;

    document.body.appendChild(picker);
    picker.addEventListener('emoji-click', event => {
        pickemojis = pickemojis.concat(event.detail.emoji.unicode);
        i = pickemojis.length - 1;
        pickemoji = (event.detail.emoji.unicode);
        document.querySelector('input').value += pickemoji;
    });
    function copyBtn() {
        var copyText = document.getElementById("emojis");
        copyText.select();
        copyText.setSelectionRange(0, 99999)
        document.execCommand("copy");
    }

</script>

<style>
    .copy{
        display: flex;
        max-width: 344px;
    }
    #emojis {
        padding: 5px;
        background: #DDD;
        border-radius: 10px;
        width: 264px;
        margin: 3px;
        height: 30px;
        border: none;
    }
    button{
        width: 100px;
        height: 30px;
        margin-top: 5px;
    }
</style>
<div id="neutralinoapp">
    <div class="copy">
        <input id="emojis" value="">
        <button id="copyText" on:click="{copyBtn}">Copy!</button>
    </div>
</div>
