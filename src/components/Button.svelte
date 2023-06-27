<script lang="ts">
    export let style: string = 'primary'
    export let type: any = 'button'
    export let disabled: boolean = false
</script>

<button {type} {disabled} class={style}>
    <slot></slot>
</button>

<style>
    button {
        color: #fff;
        border: 0;
        border-radius: 5px;
        width: 100px;
        height: 40px;
        cursor: pointer;
    }

    .primary {
        background-color: #202142;
    }

    .secondary {
        background: #ff6a95;
    }

    button:hover {
        transform: scale(0.98);
        opacity: 0.8;
    }

    button:disabled {
        background-color: #cccccc;
        color: #333;
        cursor: auto;
    }

    button:disabled:hover {
        transform: scale(1);
        opacity: 1;
    }
</style>