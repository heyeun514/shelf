<template>
    <div class="shelf-plate">
        
            <div class="line" v-bind:style="{ width: lineWidth + 'px' }"></div>
            <div class="shadow" v-bind:style="{ left: 0 + 'px', 
                                transform: 'skew(20deg)',
                                height: shadowHeight + 'px',
                                width: lineWidth + 'px'}"></div>
    </div>
        
</template>
<script>
function degrees_to_radians(degrees)
{
  var pi = Math.PI;
  return degrees * (pi/180);
}
export default {
    props: {
        lineWidth: {
            type: Number,
            default: 1000
        },
        shadowDeg: {
            type: Number,
            default: 20
        },
        shadowHeight: {
            type: Number,
            default: 100,
        }
    },
    data: () => {
        return {
            lineLeft: 0
        }
    },
    created() {
        this.lineLeft = Math.atan(this.shadowDeg) * this.shadowHeight
    },
}
</script>
<style>
.shelf-plate {
    position: absolute;
}

.shelf-plate > .line {
    position: absolute;
    background-color: white;
    height: 3px;
}

.shelf-plate > .shadow {
    position: absolute;
    background: linear-gradient(#000000, #ffffff00);
    opacity: 0.3;
    transform-origin: 50% 0%;
}
</style>

