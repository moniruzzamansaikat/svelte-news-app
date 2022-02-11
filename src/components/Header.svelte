<script>
    export let categories;
    export let activeCategory;
    import {createEventDispatcher} from 'svelte';
    
    const dispatch = createEventDispatcher();

    const handleClick = (category) => {
        dispatch('setActiveCategory', category)
        document.querySelector('input[type="checkbox"]').checked = false;
    }

</script>


<header>
    <div class="wrapper">
        <nav>
            <label for="checkbox"><img class="hamburger" src="/img/bar.svg" alt=""></label>
            <input type="checkbox" id="checkbox">
 
            <ul> 
                {#each categories as category}
                    <li 
                        class:active={category === activeCategory}
                        on:click={() => handleClick(category)}
                    >{category}</li>
                {/each}
            </ul>
        </nav>

    </div>
</header>

<style>
    header {
        background-color: #fff;
        border-bottom: 2px solid #C24924;
        max-height: 60px;
        position: fixed;
        top: 50px;
        left: 0;
        width: 100%;
        padding: 10px 0;   
    }

    header .wrapper {
        display: flex;
        align-items: center;
    }

    ul {
        display: flex;
        list-style-type: none;
    }

    ul li {
        margin:  0 8px;
        font-size: 1em;
        text-transform: capitalize;
        cursor: pointer;
    }

    ul li.active {
        padding: 4px;
        background-color: #C24924;
        border-radius: 4px;
        margin-top: -3px;
        color: #f0f0f0;
    }
    
    #checkbox {
        display: none;
    }

    img.hamburger {
        width: 40px;
        height: 40px;
        display: none;
        cursor: pointer;
    }

    @media (max-width: 992px) {
        header {
            top: 0;
            z-index: 2;
        }
        
        nav {
            width: 100%;
            display: flex;
            justify-content: flex-end;
            padding-right: 1rem;
        }
        
        ul {
            display: none;
        }
        
        #checkbox:checked + ul {
            position: absolute;
            top: 60px;
            left: 0;
            width: 100%;
            display: flex;
            flex-direction: column;
            background-color: #C24924;
            min-height: 100vh;
            justify-content: space-evenly;
            padding: 0 1rem;
            text-align: center;
            animation: animate 0.5s ease-in-out;
        }

        @keyframes animate {
            0%{
                left: -100%;
            }

            100%{
                left: 0;
            }
        }

        ul li {
            margin: 0;
            font-size: 1.2rem;
        }

        ul li:hover {
            color: #f0f0f0;
        }
        
        img.hamburger {
            display: block;
        }   
    }
</style>