<template>
    <div class="relative">
        <svg fill="none" viewBox="0 0 120 120" class="avatar">
            <path
            d="M46.332 2.115l-44 29.423A3 3 0 001 34.03V77.97a3 3 0 001.332 2.493l44 29.423a3 3 0 003.336 0l44-29.423A3 3 0 0095 77.97V34.03a3 3 0 00-1.332-2.493l-44-29.423a3 3 0 00-3.336 0z"
            :fill="`url(#prefix__pattern-${id})`"
            stroke="#000"
            strokeWidth="5"
            strokeLinecap="round"
            strokeLinejoin="round"
            />
            <defs>
            <pattern
                :id="`prefix__pattern-${id}`"
                patternContentUnits="objectBoundingBox"
                width="1"
                height="1"
            >
                <use
                :xlink:href="`#prefix__image-${id}`"
                transform="matrix(.0209 0 0 .01786 -.378 0)"
                />
            </pattern>
            <image
                :id="`prefix__image-${id}`"
                :width="Width"
                :height="Height"
                :xlink:href="ImageUrl"
            />
            </defs>
        </svg>
        <span class="h-6 w-6 absolute verified" v-if="IsVerified">
            <verified-badge></verified-badge>
        </span>
    </div>

</template>

<script>
import VerifiedBadge from "./VerifiedBadge"
import uuid from 'uuid/v1'

export default {
    name: "AvatarImage",
    components: {
        VerifiedBadge
    },
    props: {
        ImageUrl: {
            type: String,
            required: false
        },
        Height: {
            type: String,
            required: false,
            default: "56"
        },
        Width: {
            type: String,
            required: false,
            default: "84"
        },
        IsVerified: {
            type: Boolean,
            required: false,
            default: false
        }
    },
    data: () => ({
        id: uuid()
    })

}
</script>

<style>
.avatar {
    min-width: 4rem;
    min-height: 4rem;
}

.verified{
    right: 0px;
    top: 35px;
}

</style>