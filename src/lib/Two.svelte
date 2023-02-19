<div class=die>
    <div class="dot one"></div>
    <div class="dot two"></div>
</div>

<style>
    .die {
        background-color: white;
        height: 200px;
        width: 200px;
        /* display: flex; */
        /* justify-content: center;
        align-items: center; */
        border-radius: 16px;
        position: relative;
    }
    
    .dot {
        background-color: black;
        width: 15%;
        height: 15%;
        border-radius: 50%
    }
    .one {
        /* margin: 2em 0 0 2em; */
        position: absolute;
        top: 15%;
        left: 15%;
    }
    .two {
        /* margin: 5em 2em 2em 0; */
        position: absolute;
        bottom: 15%;
        right: 15%;
    }
</style>