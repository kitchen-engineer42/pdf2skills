---
name: pseudocode-programming-process
description: "Implement functions using the Pseudocode Programming Process: write high-level intent comments first, then fill in implementation code beneath each comment. Use when implementing complex logic with 3+ branches, developing functions over 20 lines, designing algorithms, or when the user asks to plan code before writing it."
---

# Pseudocode Programming Process (PPP)

Write high-level pseudocode comments as a skeleton, then fill in implementation code beneath each comment. This produces well-documented, well-structured code in a single pass.

## When to Use

- Implementing functions with complex logic (3+ branches or loops)
- Functions expected to exceed 20 lines
- Algorithm design where the approach needs to be validated before coding
- User asks to "plan", "outline", or "think through" the code first

**Skip for:** Trivial one-liners, simple getters/setters, or boilerplate code.

## Workflow

### Step 1: Write Pseudocode Comments

Outline the complete logic using plain-language comments before writing any code:

```python
def process_order(order, inventory):
    # Validate the order has at least one item and a valid customer
    
    # Check each item against current inventory levels
    
    # Calculate subtotal, apply discounts for orders over $100
    
    # Reserve inventory for confirmed items
    
    # Return order confirmation with final total and any out-of-stock items
```

**Rules for pseudocode:**
- Write at the *intent* level (what and why), not implementation level
- Each comment should map to one logical block (3-8 lines of code)
- The comments alone should read as a complete description of the algorithm

### Step 2: Validate the Design

Before writing code, review the pseudocode:

- [ ] Does it cover all inputs, including edge cases?
- [ ] Is the sequence logically correct?
- [ ] Are error/exception paths accounted for?
- [ ] Can you explain the flow to someone by reading just the comments?

If the design feels unclear or overly complex, **simplify the design first** — rewrite the pseudocode before proceeding.

### Step 3: Fill In Implementation

Write code beneath each pseudocode comment:

```python
def process_order(order, inventory):
    # Validate the order has at least one item and a valid customer
    if not order.items:
        raise ValueError("Order must contain at least one item")
    if not order.customer or not order.customer.is_active:
        raise ValueError("Valid active customer required")

    # Check each item against current inventory levels
    out_of_stock = []
    confirmed_items = []
    for item in order.items:
        if inventory.get_quantity(item.sku) >= item.quantity:
            confirmed_items.append(item)
        else:
            out_of_stock.append(item)

    # Calculate subtotal, apply discounts for orders over $100
    subtotal = sum(item.price * item.quantity for item in confirmed_items)
    discount = 0.10 if subtotal > 100 else 0.0
    total = subtotal * (1 - discount)

    # Reserve inventory for confirmed items
    for item in confirmed_items:
        inventory.reserve(item.sku, item.quantity)

    # Return order confirmation with final total and any out-of-stock items
    return OrderConfirmation(
        items=confirmed_items,
        total=total,
        discount_applied=discount,
        out_of_stock=out_of_stock,
    )
```

### Step 4: Review

- [ ] Every pseudocode comment has corresponding implementation beneath it
- [ ] No comment merely repeats the code — each explains intent
- [ ] The code matches the design; no undocumented logic was added
- [ ] Edge cases identified in Step 2 are handled

See also: [PPP Checklist](references/PPP-checklist.md) for the full preparation-through-verification checklist.
