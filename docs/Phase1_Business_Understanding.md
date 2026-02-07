VGPP: Business Understanding

A. Purpose:
1.Showcase VGPP as registered printers for SBI, and allow bank managers/ bank staff to place orders for products online
2.Facilitating Online payments and tracking
3.Build credibility and allow future business expansion, with potential for scalability if services are widened in the future.

B. Stakeholders and Users:
1.Primary users: Bank managers/ Bank staff of SBI
2.Secondary users: VGPP Admin
3.Others: Business Owner

C.Business Processes/ Domain Workflow:
(Key operations the business needs to support)

Product management
1.Define products available
2.Set prices
3.Manage stock availability (optional)

Customer Data
1.Sign up new users with branch code, phone number, and other details
2.Login for existing users

Customer Order
1.Customers select products and quantities, adding items to a cart with automatic total calculation
2.Review Order
3.Proceed to payment

Payment Processing
1.Select a payment type
2.After payment success, reference or transaction ID
3.Push order details to Recent Orders

Order Completed
1.After the shipment is sent, Assign LR to Order
2.Provide LR number and tracking URL

Notifications (optional)
1.Email confirmation for register, payment success and order placement.
2.LR numbers and tracking URL email after shipment

D. Understanding Business Requirements:
1.As there is only one service provider and one client, no multi-tenancy is needed now.
2.Limited product catalog means we can have simple catalog service.
3.Low traffic is expected which means monolith is sufficient for now.
4.Shipment via third party, so no need for complex shipment logic/ microservice.
5.Online payment option provided, so there is a need for a separate module to keep everything isolated and secured.

E. Business Rules:
1.A bank manager can place an order for their branch or other branch, as long as they give their details and place order, the order is accepted.
2.Payments must be successful before marking the order as confirmed.
3.Once the order is placed, order history should be immutable.
4.Product catalog rarely changes, only prices change sometimes

F. Defining Entities:
1.User: Manager: Manager name, Branch code, email, phone number, password
2.Product: product id, product name, product description, product price
3.Order: Order id, Order details, User, items, quantity, total price,
4.Payment: payment id, order id, amount, reference id, Shipment Option(pickup/ ship to me)
5.Shipment: LR number, Transporter, Tracking URL

G. Answering Extensilibility Questions:
1.Could this app grow to multiple banks?
Not Expected
2.Could the catalog expand to more items?
Rare
3.Could traffic spike unexpectedly?
Very limited; occasional spikes may occur for 1–2 months, with 30–40 daily users and rare days reaching up to 100 users

H. Implications:
Traffic is predictable and low which means single-server monolith is sufficient and modular design is still recommended to allow future scaling, microservice extraction, or expansion.



