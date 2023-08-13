---
title: Listview helpers
description: SCSS listview helpers
url: "/docs/cssdoc/listview"

showtoc: true
disableShare: true
hidemeta: true
---

```
.mx-listview {

    //Display listview items inline
    &.listview-inline {
        >ul {
            >li {
                display: inline;

                >.mx-dataview {
                    display: inline;

                    >.mx-dataview-content {
                        display: inline;
                    }
                }
            }
        }
    }

    //Display listview items as flex items
    &.listview-flex {
        >ul {
            display: flex;
            flex-wrap: wrap;

            >li {
                &:not(:last-child) {
                    margin-right: $spacing-medium;
                }
            }
        }
    }

    &.listview-grid {
        >ul {
            @include grid(200px, $spacing-medium);
        }
    }

    //Display listview items as inline blocks
    &.listview-inline-block {
        >ul>li {
            display: inline-block;
        }
    }

    //Ends each listview item with a comma
    &.listview-comma-separated {
        >ul>li:not(:last-child) {
            &:after {
                content: ", ";
            }
        }
    }

    //Display bullets in front of listview items
    &.listview-bullets {
        >ul {
            list-style: disc;
        }
    }

    // Hides the 'no items found' text on empty lists
    &.listview-hide-empty {
        .mx-listview-empty {
            display: none;
        }
    }

    //Hides the 'load more' button in listviews
    &.listview-hide-load-more {
        .mx-listview-loadMore {
            display: none;
        }
    }
}
```
