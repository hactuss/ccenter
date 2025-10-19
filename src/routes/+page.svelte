<script>
    import { derived } from "svelte/store";

    let ew = 0;
    let eh = 0;
    let cw = 0;
    let ch = 0;
    let center_x = 0;
    let center_y = 0;
    let length = 100;
    let ratio = 61.8;
    let calcratio = () => {
        return (length / 100) * ratio * 100;
    };

    let min = 0;
    let max = 1920;
    let calculateratio;

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
    function calc() {
        center_x = 0;
        center_y = 0;
        console.log(ew, eh);
        return ((center_x = cw / 2 - ew / 2), (center_y = ch / 2 - eh / 2));
    }
</script>
<div>
    <main id="center-calc">
        <nav>
            <div><h2>Center calculator for graphic design</h2></div>
        </nav>
        <div class="flex">
            <div class="flex flex-col w-[100%]">
                <div>
                    <label for="">canvas width</label>
                    <input
                        type="number"
                        bind:value={cw}
                        oninput={calc}
                        onchange={calc}
                    />
                </div>
                <div>
                    <label for="">canvas height</label>
                    <input type="number" bind:value={ch} oninput={calc} />
                </div>
                <div>
                    <label for="">element width</label>
                    <input type="number" bind:value={ew} oninput={calc} />
                </div>
                <div>
                    <label for="">element height</label>
                    <input type="number" bind:value={eh} oninput={calc} />
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
        <!--
        <button
            id="calculate"
            onclick={() => {
                calc();
            }}>calculate</button
        > -->
        <h1>X: {center_x} px</h1>
        <h1>Y: {center_y} px</h1>
        <div>
            <a href="https://hactuss.vercel.app">made by hactuss</a>
            <a href="https://github.com/hactuss/ccenter">Source code</a>
        </div>
    </main>
    
    <br />
    <main id="ratio-calc" style="display:hidden">
        <h2>Ratio calc</h2>
        <div class="flex flex-row">
            <div>
                <button>golden ratio (1.618)</button>
                <label for="">total length</label>
                <input
                    type="number"
                    name=""
                    id=""
                    bind:value={length}
                    onchange={calcratio}
                />
    
                <p>{calcratio}</p>
            </div>
            <div>
                <img
                    src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/50/Golden_ratio_line_percentages.svg/2880px-Golden_ratio_line_percentages.svg.png"
                    alt=""
                    id="wikipedia_img"
                />
            </div>
        </div>
    </main>
</div>
<style>
    #calculate {
        background-color: darkblue;
        color: white;
    }
</style>
