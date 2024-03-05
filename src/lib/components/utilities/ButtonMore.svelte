<script>
    export let href;
</script>



<a href="{href}" style="width: fit-content;"><slot></slot></a>


<style lang="scss">
    @import '../../styles/global.scss';

    a{
        padding: 0.5rem;
        border-radius: 10px;
        border: 2px solid $offWhite;
        z-index: 2;
        text-decoration: underline;
        text-align: center;
        color: $offWhite !important;
        &:hover{
            text-decoration: underline;
            background-color: $lightViolet;
            color: $offWhite !important;
        }
        p{
            text-decoration: underline;
            color: $offWhite !important;
        }

    }

    a:hover p {
    color: #e1d7cb !important;
}
</style>