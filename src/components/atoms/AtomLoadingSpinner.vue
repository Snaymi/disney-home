<template>
    <div class="spinner">
        <div class="blob top"></div>
        <div class="blob bottom"></div>
        <div class="blob left"></div>
        <div class="blob move-blob"></div>
    </div>
</template>

<style scoped>
.spinner {
    position: absolute;
    width: 30px;
    height: 30px;

    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.blob {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    border: 2px solid #fff;

    width: 10px;
    height: 10px;
    border-radius: 50%;
}

.blob.top {
    top: 0;
    animation: blob-top 1s infinite ease-in;
}

.blob.bottom {
    top: 100%;
    animation: blob-bottom 1s infinite ease-in;
}

.blob.left {
    left: 0;
    animation: blob-left 1s infinite ease-in;
}

.move-blob {
    position: absolute;
    background: #fff;
    border-radius: 50%;
    width: 10px;
    height: 10px;
    top: 0;
    left: 50%;
    transform: translate(-50%, 0);
    animation: blob-spinner-mover 1s infinite ease-in;
}

/* Keyframes convertidos */
@keyframes blob-bottom {

    25%,
    50%,
    75% {
        top: 50%;
        left: 100%;
    }

    100% {
        top: 0;
        left: 50%;
    }
}

@keyframes blob-left {
    25% {
        top: 50%;
        left: 0;
    }

    50%,
    100% {
        top: 100%;
        left: 50%;
    }
}

@keyframes blob-top {
    50% {
        top: 0;
        left: 50%;
    }

    75%,
    100% {
        top: 50%;
        left: 0;
    }
}

@keyframes blob-spinner-mover {

    0%,
    100% {
        top: 0;
        left: 50%;
    }

    25% {
        top: 50%;
        left: 100%;
    }

    50% {
        top: 100%;
        left: 50%;
    }

    75% {
        top: 50%;
        left: 0;
    }
}
</style>
