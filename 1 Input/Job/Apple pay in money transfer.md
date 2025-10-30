
Models:
`TransactionPayment` - transaction_payment.dart
`TransactionRequestDataModel` - transaction_request_datamodel.dart


Service - set_up_transaction_api_service.dart:
- `postTransaction` we send here `TransactionRequestDataModel`

Money Transfer Helper - money_transfer_helper.dart:
- `submitTransaction` we send here `TransactionRequestDataModel`

Money Transfer Manager - money_transfer_manager.dart:
- `sendTransaction` we construct here `TransactionRequestDataModel` from transfer - `MoneyTransferRequest` and other parameters.
- Here is what happens inside construction:
	- we get `payment` parameter from `TransactionPayment.fromTransfer(transfer: transfer)`
	- inside `TransactionPayment.fromTransfer` we set `mobilePayment` to `transfer.selectedNativePaymentMethod!.nativePaymentResponse` (later I will write where did we set it)
	- inside `TransactionPayment.toJson`  we have 
```
if (mobilePayment != null) {
	data['mobile_payment'] = {
		'token': jsonEncode(mobilePayment),
	};
}
```

Step Review Order View Model - step_review_order_view_model.dart:
- `makeTransfer` we trigger `sendTrasaction` and pass here transaction data

Step Review Order - step_review_order.dart:
- `_onConfirmationResult` we trigger first `setNativePaymentResponse` from `StepReviewOrderViewModel` to set the response we got from `SuccessPaymentResult` that we got. We put it inside transaction, into `selectedNativePaymentMethod.nativePaymentResponse`
- then trigger `makeTransfer`


For UI
take a look at that files in sequence:
- `mt_payment_methods_bottomsheet_controller.dart
- `select_payment_method_bottomsheet.dart`
- `selectable_payment_methods_other_list_view.dart`
- `inapp_pay.dart

Links:

202510301642

