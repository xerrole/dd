# Validate field in django form

In django form, we can validate a field by adding a `clean_[fieldname]()` method. This validation can display the error message under the input field in django admin site.

    class FeaturePriceForm(forms.ModelForm):
        def clean_unit(self):
            # unit_price = self.cleaned_data['unit_price']
            unit = self.cleaned_data['unit']
            if self.cleaned_data['unit_price'] and not unit:
                raise forms.ValidationError(_('Please select unit for price.'))
            return unit

    class FeaturePriceAdmin(admin.ModelAdmin):
        form = FeaturePriceForm

Moreover, we can also add a validate method named `clean()` in django model. Errors from this method will be appended to form.non_field_errors, and in django admin site, these errors will be displayed on the top of the page.


# Filter data with field in a list, case-insensitive

solution1

    name_list = ['Alpha', 'bEtA', 'omegA']
    q_list = map(lambda n: Q(name__iexact=n), name_list)
    q_list = reduce(lambda a, b: a | b, q_list)
    MyModel.objects.filter(q_list)


solution2

    name_list = ['Alpha', 'bEtA', 'omegA']
    results = MyModel.objects.none()
    for name in name_list:
        results |= MyModel.objects.filter(name__iexact=name)
