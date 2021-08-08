<script>
  import { Container, CardNumber, CardExpiry, CardCvc } from './components'
  const stripe = Stripe('pk_test_EFUTAJ2pGPBKqTiQPTiGIGsD');

  let container

  async function submit() {
    const card = container.getElement()
    const result = await stripe.createToken(card)

    alert(`Got: ${result.token.card.id}`)
  }
</script>

<Container {stripe} bind:this={container}>
  <form on:submit|preventDefault={submit}>
    <CardNumber/>
    <CardExpiry/>
    <CardCvc/>

    <button>Pay</button>
  </form>
</Container>

<style>
</style>
