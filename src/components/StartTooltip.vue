<template>
    <Tooltip :tooltip-id="tooltipId">
        *
        <template slot="toopltip-content">
            <span class="toopltip-content-star">*</span>
            <div class="toopltip-content-text">
                <p>
                    World Health Organization. Global Atlas on Cardiovascular
                    Diseases Prevention and Control, 2011.
                </p>
            </div>
        </template>
    </Tooltip>
</template>

<script>
    import Tooltip from './Tooltip/Tooltip'

    export default {
        name: 'TestResultTooltip01',
        props: ['tooltipId'],
        components: {
            Tooltip
        }
    }
</script>
