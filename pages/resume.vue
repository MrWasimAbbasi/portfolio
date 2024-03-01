<template>
  <div>
    <h1>File</h1>

    <PDFViewer
      :source="url"
      style="height: 100vh"
      @download="handleDownload"
    />
    
  </div>
</template>

<script>
import PDFViewer from 'pdf-viewer-vue'

export default {
  components: {
    PDFViewer,
  },

  data() {
    return {
      url: './Resume Muhammad Waseem, Full-Stack(Laravel, Vue) Developer.pdf',
    }
  },
}
</script>
