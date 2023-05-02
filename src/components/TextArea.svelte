<script>
  import { isValidInput } from '../store.js'
  import { checkIsEnglish } from '../services/ia.js'

  const handleChange = async (e) => {
    const { value }  = e.target
    const isValid = value.length > 0
    if(!isValid) {
      isValidInput.set(false)
      return
    }

    const isEnglish = await checkIsEnglish(value)
    isValidInput.set(isEnglish)
  }

</script>

<textarea 
  on:input={handleChange}
  id="result"
  placeholder="Write here what you want to correct..."
  name="comment"
  rows="4"
  cols="40"
  class="flex-1 w-full px-4 py-2 mt-4 hover:bg-gray-50 focus:bg-gray-50 text-base text-gray-700 placeholder-gray-400 bg-white border border-gray-300 rounded-lg appearance-none focus:outline-none focus:ring-2 focus:ring-zinc-300 focus:border-transparent shadow-md" 
/>
