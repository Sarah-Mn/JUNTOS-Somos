<template>
  <div class="pagination-container">
    <ul class="pagination">
      <li class="pagination-item">
        <button
          class="first"
          type="button"
          @click="onClickFirstPage"
          :disabled="isInFirstPage"
        >
          First
        </button>
      </li>

      <li class="pagination-item">
        <button
          class="nav-btn"
          type="button"
          @click="onClickPreviousPage"
          :disabled="isInFirstPage"
        >
          <i class="fas fa-angle-left"></i>
        </button>
      </li>

      <!-- Visible Buttons Start -->

      <li v-for="(page, index) in pages" :key="index" class="pagination-item">
        <button
          class="pages"
          type="button"
          @click="onClickPage(page.name)"
          :disabled="page.isDisabled"
          :class="{ active: isPageActive(page.name) }"
        >
          {{ page.name }}
          <div class="active-page"></div>
        </button>
      </li>

      <!-- Visible Buttons End -->

      <li class="pagination-item">
        <button
          class="nav-btn"
          type="button"
          @click="onClickNextPage"
          :disabled="isInLastPage"
        >
          <i class="fas fa-angle-right"></i>
        </button>
      </li>

      <li class="pagination-item">
        <button
          class="last"
          type="button"
          @click="onClickLastPage"
          :disabled="isInLastPage"
        >
          Last
        </button>
      </li>
    </ul>
  </div>
</template>

<script lang="ts" setup>
import { defineProps, computed, defineEmits } from "vue";

const props = defineProps({
  maxVisibleButtons: {
    type: Number,
    required: false,
    default: 3,
  },

  totalPages: {
    type: Number,
    required: true,
  },
  perPage: {
    type: Number,
    required: true,
  },
  currentPage: {
    type: Number,
    required: true,
  },
});

const emit = defineEmits(["pagechanged"]);

const startPage = computed(() => {
  if (props.currentPage === 1) {
    return 1;
  }
  if (props.currentPage === props.totalPages) {
    return props.totalPages - props.maxVisibleButtons;
  }
  return props.currentPage - 1;
});

const pages = computed(() => {
  let range = [];

  for (
    let i = startPage.value;
    i <=
    Math.min(startPage.value + props.maxVisibleButtons - 1, props.totalPages);
    i++
  ) {
    range.push({
      name: i,
      isDisabled: i === props.currentPage,
    });
  }

  return range;
});

const isInFirstPage = computed(() => {
  return props.currentPage === 1;
});
const isInLastPage = computed(() => {
  return props.currentPage === props.totalPages;
});

const onClickFirstPage = () => {
  emit("pagechanged", 1);
};
const onClickPreviousPage = () => {
  emit("pagechanged", props.currentPage - 1);
};
const onClickPage = (page: number) => {
  emit("pagechanged", page);
};
const onClickNextPage = () => {
  emit("pagechanged", props.currentPage + 1);
};
const onClickLastPage = () => {
  emit("pagechanged", props.totalPages);
};

const isPageActive = (page: number) => {
  return props.currentPage === page;
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap");

.pages {
  background-color: transparent;
  border: none;
  color: rgb(196, 195, 195);
  cursor: pointer;
  font-family: "Roboto", sans-serif;
  font-size: 1.2rem;
}

.nav-btn {
  background-color: #4a4a4a;
  border: none;
  border-radius: 50%;
  color: #ffffff;
  cursor: pointer;
}

.pagination {
  list-style-type: none;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.pagination-item {
  display: inline-block;
}

.last,
.first {
  background-color: transparent;
  color: #4a4a4a;
  border: none;
  cursor: pointer;
  font-family: "Roboto", sans-serif;
  font-size: 1.5rem;
  margin: 0 0.5rem;
}

.fa-angle-right,
.fa-angle-left {
  font-size: 1.5rem;
}

.active {
  color: #000000;
}

.active .active-page {
  height: 3.5px;
  width: 1.5rem;
  background-color: #4a4a4a;
  border-radius: 1rem;
}

@media only screen and (max-width: 576px) {
  .pages {
    font-size: 1rem;
    margin: 1rem;
  }

  .last,
  .first {
    font-size: 1rem;
  }

  .pagination {
    width: 100%;
  }

  .fa-angle-right,
  .fa-angle-left {
    font-size: 2rem;
  }

  .nav-btn {
    border-radius: 50%;
    width: 2rem;
  }
}

@media only screen and (min-width: 576px) and (max-width: 768px) {
  .pages {
    font-size: 1rem;
    margin: 1rem;
  }

  .last,
  .first {
    font-size: 1rem;
  }

  .pagination {
    width: 100%;
  }

  .fa-angle-right,
  .fa-angle-left {
    font-size: 2rem;
  }

  .nav-btn {
    border-radius: 50%;
    width: 2rem;
  }
}

@media only screen and (min-width: 768px) and (max-width: 992px) {
  .pages {
    font-size: 1rem;
    margin: 1rem;
  }

  .last,
  .first {
    font-size: 1rem;
  }

  .pagination {
    width: 100%;
  }

  .fa-angle-right,
  .fa-angle-left {
    font-size: 2rem;
  }

  .nav-btn {
    border-radius: 50%;
    width: 2rem;
  }
}

@media only screen and (min-width: 993px) {
  .pages {
    font-size: 1rem;
    margin: 1rem;
  }

  .last,
  .first {
    font-size: 1rem;
  }

  .pagination {
    width: 100%;
  }

  .fa-angle-right,
  .fa-angle-left {
    font-size: 2rem;
  }

  .nav-btn {
    border-radius: 50%;
    width: 2rem;
  }
}
</style>
