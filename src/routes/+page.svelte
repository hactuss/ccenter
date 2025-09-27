<script>
    let ew = 0;
    let eh = 0;
    let cw = 0;
    let ch = 0;
    let center_x = 0;
    let center_y = 0;

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
    function pre_HD() {
        cw = 1280;
        ch = 720;
    }
</script>

<div id="main_container">
    <nav class="flex">
        <h2>Center calculator for graphic design</h2>
    </nav>
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
            <h3>preset canvas resolutions</h3>
            <div>
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
                <button
                    onclick={() => {
                        pre_HD();
                    }}>HD</button
                >
            </div>
        </div>
    </div>
    <button
        id="calculate"
        onclick={() => {
            center_x = cw / 2 - ew / 2;
            center_y = ch / 2 - eh / 2;
        }}>calculate</button
    >
    <h1>X: {center_x} px</h1>
    <h1>Y: {center_y} px</h1>
    <div>
        <a href="https://hactuss.vercel.app">made by hactuss</a>
        <a href="https://github.com/hactuss/ccenter">Source code</a>
    </div>
</div>

<style>
    #calculate {
        background-color: darkblue;
        color: white;
    }
</style>
