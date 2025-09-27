<script>
    let ew = 1;
    let eh = 1;
    let cw = 1;
    let ch = 1;
    let center_x = 2;
    let center_y = 2;

    //presets
    function pre_A4() {
        cw = 2480;
        ch = 3508;
        return 1;
    }
    function pre_FullHD() {
        cw = 1920;
        ch = 1080;
        return 1;
    }
    let dropdownmenu = "block";
    function changedropdown() {
        switch (dropdownmenu) {
            case "none":
                dropdownmenu = "block";
                break;
            case "block":
                dropdownmenu = "none";
                break;
        }
    }
</script>

<div class="">
    <h1>Center Calculator</h1>
    <div class="flex">
        <div class="flex flex-col w-[100%]">
            <div>
                <label for="">element width</label>
                <input type="number" value={ew} />
            </div>
            <div>
                <label for="">element height</label>
                <input type="number" value={eh} />
            </div>
            <div>
                <label for="">canvas width</label>
                <input type="number" value={cw} />
            </div>
            <div>
                <label for="">canvas height</label>
                <input type="number" value={ch} />
            </div>
        </div>
        <div class="w-[100%]">
            <button
                class=""
                onclick={() => {
                    changedropdown();
                }}
            >
                <h2>presets</h2>
            </button>
            <div style="display: {dropdownmenu}; border: solid black;">
                <button
                    onclick={() => {
                        pre_A4();
                    }}>A4</button
                >
                <button
                    onclick={() => {
                        pre_FullHD();
                    }}>Full HD</button
                >
            </div>
        </div>
    </div>
    <button
        onclick={() => {
            center_x = cw / 2 - ew / 2;
            center_y = ch / 2 - eh / 2;
        }}>calculate</button
    >
    <h1>X: {center_x}</h1>
    <h1>Y: {center_y}</h1>
</div>
<p>by hactuss</p>
