<script>
    // import items from './+page'
    import Item from './Item.svelte'

    // Minitialize
    let items = [{ id: 1, label: 'Item ' + 1, price: 0, perc: 0, discountedPrice: 0}];
    let paid;
    let totalNormalPrice;
    let showResults;

    function deleteField(event) {
        items = items.filter((e) => e.id != event.detail.objAttributes.id);
        let updateId = 1;
        items.forEach((e) => {
            e.id = updateId;
            updateId++;
        });
    }

    // add new field
    function addMoreField() {
        var n = items.length;
        items[n] = { id: n + 1, label: 'Item ' + (n + 1), price: 0, perc: 0, discountedPrice: 0 };
    }

    function clear() {
        showResults = false;
        items = [{ id: 1, label: 'Item ' + 1, price: 0, perc: 0, discountedPrice: 0 }];
        paid = null;
    }

    function calculate() {
        showResults = true
        totalNormalPrice = items.map(e => e.price).reduce((a, b) => a + b, 0);

        items.forEach((e) => {
            e.perc = e.price / totalNormalPrice;
            e.discountedPrice = e.perc * paid;
        })

        console.log(items)
        console.log(totalNormalPrice)
    }

</script>

<div class="calculator">
    
    <div class="items">
        {#each items as i}
            <Item objAttributes={i} on:deleteItem={deleteField}/>
        {/each}
    </div>

    <div class="settings">
        
        <div>
            <button on:click={clear} aria-label="Clear">
                Clear
            </button>

            <button on:click={addMoreField} aria-label="Add item">
                Add item
            </button>

            <button on:click={calculate} aria-label="Calculate" class="accent">
                Calculate
            </button>            
        </div>

        <!-- Total paid -->
        <div>
            <label for="total-paid">
                Total paid (after discount)
            </label>
            <input
                placeholder=50000
                type="number"
                id="total-paid"
                bind:value={paid}
                required
            />
        </div>

        <!-- Result -->
        {#if showResults}
        <div class="result">
            <p>Total amount paid (after discount): {paid}</p>

            <p>Total amount for normal price: {totalNormalPrice}</p>

            <ol>
                {#each items as i}
                    <li>
                        <p>{i.label}</p>
                        <p>Normal price: {i.price}</p>
                        <p>Discouted price: {i.discountedPrice}</p>
                    </li>
                {/each}
            </ol>
        </div>
        {/if}
    </div>

    
</div>

<style>
    .calculator {
        display: flex;
        flex-direction: column-reverse;
        row-gap: 24px;
        width: 100%;
        /* max-width: ; */
    }

    @media (min-width: 768px){
        .calculator {
            flex-direction: row;
            column-gap: 24px;
        }
    }

    .settings div:not(:last-child) {
        margin-bottom: 16px;
    }

    .items {
        flex: 4;
    }

    .settings { 
        flex: 2;
    }
</style>