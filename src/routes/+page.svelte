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

<!--
<main id="MAIN">
    <main id="center-calc">
        <nav>
            <div><h2>Center calculator for graphic design</h2></div>
        </nav>
        <div class="flex">
            <div class="flex flex-col">
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
        >
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
</main>
-->
<main id="newMain">
    <div id="titlebar">
        <h2>Center Calculator for graphic design</h2>
        <a href="https://hactuss.vercel.app">made by hactuss</a>
        <a href="https://github.com/hactuss/ccenter">Source code</a>
    </div>
    <section>
        <div id="buttonholder">
            <div class="flex flex-col" id="inputs">
                <div class="flex">
                    <div>
                        <label for="">canvas width</label>
                        <input type="number" bind:value={cw} oninput={calc} />
                    </div>
                    <div>
                        <label for="">canvas height</label>
                        <input type="number" bind:value={ch} oninput={calc} />
                    </div>
                </div>

                <div class="flex">
                    <div>
                        <label for="">element width</label>
                        <input type="number" bind:value={ew} oninput={calc} />
                    </div>
                    <div>
                        <label for="">element height</label>
                        <input type="number" bind:value={eh} oninput={calc} />
                    </div>
                </div>
            </div>
            <div class="w-[100%]" id="presets">
                <h3>preset canvas resolutions</h3>
                <div>
                    <button onclick={pre_A4}>A4 [2480 x 3508]</button>
                    <button onclick={pre_FullHD}>Full HD [1920 x 1080]</button>
                    <button onclick={pre_HD}>HD [1280 x 720]</button>
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
    </section>
</main>

<style>
    #MAIN {
        background-color: rgb(50 50 50);
    }
    #newMain {
        border: 2px solid white;
        border-radius: 0.2rem;

        background: rgb(0 0 0);
    }
    #titlebar {
        font-family: monospace;
        color: white;
        background: #141414;
        background: linear-gradient(
            0deg,
            rgba(20, 20, 20, 1) 0%,
            rgba(50, 50, 50, 1) 50%,
            rgba(100, 100, 100, 1) 100%
        );
        border: solid black 3px;
        border-radius: 3px;
    }
    section {
        color: white;
    }

    #buttonholder {
        display: flex;
    }
</style>
