<template>
  <Card class="my-5">
    <CardHeader>
      <CardTitle class="text-2xl font-bold">{{ title }}</CardTitle>
      <Separator />
    </CardHeader>
    <CardContent class="text-ellipsis text-secondary-foreground/70">{{ summary }}</CardContent>
    <CardFooter>
        <Button class="w-full">Read more</Button>
    </CardFooter>
  </Card>
</template>

<script lang="ts" setup>
defineProps<{
    title: string
    summary: string
}>()
</script>
