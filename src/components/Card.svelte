<script lang="ts">
    interface Button {
        name: string;
        icon?: string;
        href: string;
    }

    interface Social {
        name: string;
        icon: string;
        href: string;
    }

    interface CardItemProps {
        bgColor: string;
        primaryTextColor: string;
        secTextColor: string;
        buttonColor: string;
        avatar: string;
        userName: string;
        position: string;
        phoneNum: string;
        email: string;
        phyAddress?: string;
        mainButtons: Button[];
        socials?: Social[];
    }

    const cardItems: CardItemProps = {
        bgColor: "#FFFFFF",
        primaryTextColor: "#1F2937",
        secTextColor: "#FFFFFF",
        buttonColor: "#EA580C",
        avatar: "/assets/avatar.png",
        userName: "John Doe",
        position: "Software Developer",
        phoneNum: "+1 214 345 6778",
        email: "jd@example.com",
        phyAddress: "333 Freemont Rd, San Francisco",
        mainButtons: [
            { name: "Portfolio", icon: "", href: "#" },
            { name: "Contact", icon: "", href: "#" },
            { name: "Blog", icon: "", href: "#" },
        ],
        socials: [
            { name: "facebook", icon: "/assets/facebook.svg", href: "https://facebook.com" },
            { name: "linkedin", icon: "/assets/linkedin.svg", href: "https://linkedin.com" },
            { name: "x", icon: "/assets/x.svg", href: "https://x.com" }
        ]
    }
</script>

<style>
    .card {
        background-color: var(--bgColor);
        color: var(--primaryTextColor);
    }
    .primary-text {
        color: var(--primaryTextColor);
    }
    .main-button {
        background-color: var(--buttonColor);
        color: var(--secTextColor);
    }
</style>

<div class="card flex justify-center h-full w-full" style="--bgColor: {cardItems.bgColor}; --primaryTextColor: {cardItems.primaryTextColor}; --secTextColor: {cardItems.secTextColor}; --buttonColor: {cardItems.buttonColor};">
    <div class="py-16 flex flex-col justify-center space-y-6 w-1/2">
        <div class="w-full flex justify-center items-center rounded-full">
            <img src={cardItems.avatar} alt={cardItems.userName} class="w-32 h-32 rounded-full bg-cyan-300" />
        </div>
        <div class="space-y-4 flex flex-col justify-center">
            <h2 class="primary-text text-lg text-center font-bold">{cardItems.userName}</h2>
            <p class="primary-text text-center">{cardItems.position}</p>
            <a href={`mailto:${cardItems.email}`} target="_blank" class="underline text-center">
                {cardItems.email}
            </a>
            <a href={`tel:${cardItems.phoneNum}`} target="_blank" class="underline text-center">
                {cardItems.phoneNum}
            </a>
            <p class="primary-text text-center">{cardItems.phyAddress || ""}</p>
        </div>
        {#if cardItems.socials}
            <div class="mt-4 flex flex-wrap gap-2 justify-center">
                {#each cardItems.socials as social}
                    <div class="flex items-center justify-center h-12 w-12 bg-transparent rounded-lg">
                        <a href={social.href} class="social-icon" target="_blank">
                            <img src={social.icon} alt={social.name} class="w-6 h-6" />
                        </a>
                    </div>
                {/each}
            </div>
        {/if}
        <div class="flex flex-col space-y-4">
            {#each cardItems.mainButtons as button}
                <a href={button.href} class="main-button btn flex items-center space-x-1 p-4 hover:bg-cyan-300 font-medium rounded justify-around">
                    {#if button.icon}
                        <img src={button.icon} alt={button.name} class="w-4 h-4" />
                    {/if}
                    <span>{button.name}</span>
                </a>
            {/each}
        </div>
    </div>
</div>
